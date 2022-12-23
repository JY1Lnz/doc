# ID3D12Device

## CreateCommittedResource
```C++
HRESULT ID3D12Device::CreateCommittedResource(
	const D3D12_HEAP_PROPERTIES* pHeapProperties,
	D3D12_HEAP_FLAGS HeapFlags,
	const D3D12_RESOURCE_DESC* pDesc,
	D3D12_RESOURCE_STATES InitialResourceState,
	const D3D12_CLEAR_VALUE* pOptimiedClearValue,
	REFIID riidResource,
	void **ppvResource
);

typedef struct D3D12_HEAP_PROPERTIES{
	D3D12_HEAP_TYPE TYPE;
	D3D12_CPU_PAGE_PROPERTY CPUPageProperty;
	D3D12_MEMORY_POOL MemoryPoolPreference;
	UINT CreationNodeMask;
	UINT VisibleNodeMask;
} D3D12_HEAP_ProPERTIES;
```
1. pHeapProperties：（资源欲提交的堆）堆所具有的属性，目前只关注D3D12_HEAP_TYPE这属性。
	1. D3D12_HEAP_TYPE_DEFAULT：默认堆，向这里提交的资源只有GPU能访问。
	2. D3D12_HEAP_TYPE_UPLOAD：上传堆，向这里提交的都是经CPU上传至GPU的资源。
	3. D3D12_HEAP_TYPE_READBACK：回读堆，向这里提交的资源都是需要由CPU读取的资源。
2. HeapFlags：与堆有关的额外选项标志，通常设置 D3D12_HEAP_FLAG_NONE。
3. pDesc：指向一个D3D12_RESOURCE_DESC的指针，用了描述待建的资源。
4. InitialResourceState：资源的初始状态
5. pOptimiedClearValue：用于清除资源的优化值，
6. riidResource：希望获得的ID3D12Resource接口的COM ID
7. ppvResource：返回一个指向ID3D12Resource接口的指针，即新建的资源