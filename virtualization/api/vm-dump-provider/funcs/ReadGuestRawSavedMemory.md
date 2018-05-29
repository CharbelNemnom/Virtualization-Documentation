# ReadGuestRawSavedMemory
**Note: These APIs are publicly available as of Windows 1803 (10.0.17134.48). You can build your project against these APIs, but the DLL for linking is missing from the SDK. You should use the latest SDK and associated DLL released with Windows Insider to run your application**

## Syntax
```C
HRESULT 
WINAPI 
ReadGuestRawSavedMemory( 
    _In_        VM_SAVED_STATE_DUMP_HANDLE  VmSavedStateDumpHandle, 
    _In_        UINT64                      RawSavedMemoryOffset, 
    _Out_writes_bytes_(BufferSize) LPVOID   Buffer, 
    _In_        UINT32                      BufferSize, 
    _Out_opt_   UINT32*                     BytesRead 
    ); 
```
### Parameters

`VmSavedStateDumpHandle`

Supplies a handle to a dump provider instance.

`RawSavedMemoryOffset`

Byte offset on the raw saved memory from where to start reading.

`Buffer`

Returns the raw memory read on the current raw memory offset.

`BufferSize`

Supplies the requested byte count to read.

`BytesRead`

Optionally returns the bytes actually read.

## Return Value

If the operation completes successfully, the return value is `S_OK`.

## Remarks

Reads raw memory from the saved state file. This function reads raw memory from the saved state file as if it were a flat memory layout, regardless of the guest memory layout. If BytesRead returns something lower than BufferSize, then the end of memory has been reached. 