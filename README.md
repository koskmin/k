# k
import socket

def send_message(sock, message):
    try:
        sock.send(message.encode('utf-8'))
        response = sock.recv(1024).decode('utf-8')
        print(f"Server response: {response}")
    except Exception as e:
        print(f"Error: {e}")

def main():
    host = '127.0.0.1'
    port = 12345

    client_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    client_socket.connect((host, port))

    while True:
        message = input("Enter a message (type 'exit' to quit): ")
        if message.lower() == 'exit':
            break
        send_message(client_socket, message)

    client_socket.close()

if __name__ == "__main__":
    main()
