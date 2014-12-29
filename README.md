Chrome-WebSocket-Notification-Extension-Example
===============================================

## ˵��

һ���򵥵� Chrome ��� WebSocket ��֪ͨ������չ

����[�����Ƽ򵥵� WebSocket ������ + Chrome ֪ͨ���Ͳ����](http://note.laobubu.net/archives/websocket-server-and-chrome-notification-extension/) һ��ʳ�á�

����ʹ�õ� WebSocket ���Է��������� [http://lab.laobubu.net/ws_create.html](http://lab.laobubu.net/ws_create.html) ��

����׼���˼򵥵� `WSKeeper` ���������Զ������� WebSocket ���ӣ��Լ� `NManager` ���������͹���֪ͨ��

## ͵������

�����ֱ��ʹ�������չ��Ȼ���޸ĳ����Լ���֪ͨ��չ������������£�

1. �޸� `manifest.json` �еĵ�ַ
2. �޸� `background.js` ���� `Main Code` ���µĴ���
3. �޸�ͼ��

## ������ĵ�

### WSKeeper��

�����Զ������� WebSocket ���ӣ������÷����£�
```
var ws = new WSKeeper(
	"ws://lab.laobubu.net:8000",	//websocket url
	"json-message",					//websocket protocol
	function onMessage(obj) {		//websocket JSON message handler
		//handle JSON object
	}
);
```

���Ҫ�Ͽ����ӣ�ʹ�� `ws.disconnect()` ���ɡ�

### NManager��

���𴴽��͹���֪ͨ��
```
var nman = new NManager("sample-prefix-");	//prefix must be unique
```

�������һ��֪ͨ
```
nman.remove(notificationId)
```

ʹ���������Լ򵥴ֱ��ش�������֪ͨ������������ص���֪ͨ�� ID
```
nman.create("����", "��������", {})
```

Ҳ������һЩ������
```
var options = {
	url:	"",	//(��ѡ) �������ʱ�Զ��򿪵� URL
	buttons: [	//(��ѡ) ��ť������
		{title: "Button1",	onclick: function(notificationId, index){alert("Hello from message #"+nid)} },
		{title: "Button2", 	url: "http://laobubu.net"}
		//һ����ť��������� title ����ť���֣�
		//��ѡ iconUrl ��ʾ��ťͼ�� URL
		//��ѡ onclick ����ť������ʱ�Ļص����������� url ��ʾ��ť������ʱ�򿪵� URL
	]
};
nman.create(obj.title, obj.data, options);
```