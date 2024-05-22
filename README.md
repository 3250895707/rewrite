# rewrite
import struct

def is_little_endian():
    return struct.pack('@I', 0x12345678)[0] == 0x78

def uval(buffer, offset):
    return struct.unpack_from('>I' if not is_little_endian() else '<I', buffer, offset)[0]

def ival(buffer, offset):
    return struct.unpack_from('>i' if not is_little_endian() else '<i', buffer, offset)[0]

def sival(buffer, offset, value):
    struct.pack_into('>i' if not is_little_endian() else '<i', buffer, offset, value)

def ival64(buffer, offset):
    return struct.unpack_from('>q' if not is_little_endian() else '<q', buffer, offset)[0]

def sival64(buffer, offset, value):
    struct.pack_into('>q' if not is_little_endian() else '<q', buffer, offset, value)

def cval(buffer, offset):
    return buffer[offset]
