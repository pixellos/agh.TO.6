```plantuml
left to right direction
skinparam packageStyle rectangle


actor Jednostka_Administracyjna

rectangle broker_komunikatow {
  (zarejestrowanie obsługi wiadomości) -- Jednostka_Administracyjna
  (pobranie kanału dla typu) --   (zarejestrowanie obsługi wiadomości) :include
  (wysłanie komunikatu) -- Jednostka_Administracyjna
  (odbiór komunikatu) -- Jednostka_Administracyjna
}



```

```plantuml
class Message {
    type: Number
}

interface IChannelReceiver {
   onReceive: EventHandlers

}


interface IChannelSender {
   send(m:Message)
}

class Type {
    id: String
}

class ChannelFactory {
  Channel getWriterChannel(type :Type)
  Channel getReaderChannel(type: Type)
}

class Channel implements IChannelReceiver, IChannelSender {
   type : Type
   send(m:Message)

   onReceive: EventHandlers
}

class ChannelCollection implements Channel{
    register(channel: IChannelSender)
    register(channel: IChannelReceiver)
}


ChannelFactory -- Channel



```