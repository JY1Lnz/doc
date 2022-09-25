# Wwise
## API
### PostEvent
https://www.audiokinetic.com/zh/library/edge/?source=SDK&id=namespace_a_k_1_1_sound_engine_a41e9ef8d42951871fe4a8ae58a29a68e.html#a41e9ef8d42951871fe4a8ae58a29a68e
参数列表
- AkUniqueID
	使用的事件id
- AkGameObjectID
	接受音频的gameobject
- AkUint32
	不知道 
- AkCallbackFunc
	当这个事件完成之后的回调函数，接受三个参数
	- object
		下文传进去的参数
	- AkCallbakcType
		不知道
	- AkCallbackInfo
		不知道
- object
	一个对象，会作为回调函数的入参