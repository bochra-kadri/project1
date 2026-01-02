from Crypto.Cipher import AES, DES
from Crypto.Random import get_random_bytes
import time

def pad_aes(data):
    while len(data) % 16 != 0:
        data += b' '
    return data

def pad_des(data):
    while len(data) % 8 != 0:
        data += b' '
    return data

message = b"Security and Privacy Mini Project"

# AES
key_aes = get_random_bytes(16)
aes_message = pad_aes(message)
cipher_aes = AES.new(key_aes, AES.MODE_ECB)

start_time = time.time()
encrypted_aes = cipher_aes.encrypt(aes_message)
aes_enc_time = time.time() - start_time

start_time = time.time()
decrypted_aes = cipher_aes.decrypt(encrypted_aes)
aes_dec_time = time.time() - start_time

# DES
key_des = get_random_bytes(8)
des_message = pad_des(message)
cipher_des = DES.new(key_des, DES.MODE_ECB)

start_time = time.time()
encrypted_des = cipher_des.encrypt(des_message)
des_enc_time = time.time() - start_time

start_time = time.time()
decrypted_des = cipher_des.decrypt(encrypted_des)
des_dec_time = time.time() - start_time

print("AES Encryption Time:", aes_enc_time)
print("AES Decryption Time:", aes_dec_time)
print("DES Encryption Time:", des_enc_time)
print("DES Decryption Time:", des_dec_time)

