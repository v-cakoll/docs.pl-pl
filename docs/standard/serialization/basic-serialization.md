---
title: Serializacja podstawowa
ms.date: 03/30/2017
helpviewer_keywords:
- binary serialization, basic serialization
- serialization, basic serialization
ms.assetid: d899d43c-335a-433e-a589-cd187192984f
dev_langs:
- CSharp
ms.openlocfilehash: cb42c265d9057ea4fdb76e72fc9cdb2368309cae
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44181579"
---
# <a name="basic-serialization"></a>Serializacja podstawowa

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

Najprostszym sposobem wybierz klasę serializacji jest do oznaczania za pomocą <xref:System.SerializableAttribute> w następujący sposób.  
  
```csharp  
[Serializable]  
public class MyObject {  
  public int n1 = 0;  
  public int n2 = 0;  
  public String str = null;  
}  
```  
  
Poniższy przykład kodu pokazuje, jak wystąpienie tej klasy może być serializowany w taki sposób, w pliku.  
  
```csharp  
MyObject obj = new MyObject();  
obj.n1 = 1;  
obj.n2 = 24;  
obj.str = "Some String";  
IFormatter formatter = new BinaryFormatter();  
Stream stream = new FileStream("MyFile.bin", FileMode.Create, FileAccess.Write, FileShare.None);  
formatter.Serialize(stream, obj);  
stream.Close();  
```  
  
W tym przykładzie zastosowano binarne programu formatującego przeprowadzić serializacji. Wszystko, czego potrzebujesz, aby zrobić jest utworzenie wystąpienia strumienia i chcesz użyć, a następnie wywołać program formatujący **Serialize** metody na element formatujący. Strumień i do serializacji obiektu są dostarczane jako parametry do tego połączenia. Chociaż nie jawnie wspomniane w tym przykładzie, wszystkie zmienne składowe klasy będzie serializowana — nawet zmienne oznaczone jako prywatne. W tym aspekt serializacji binarnej różni się od <xref:System.Xml.Serialization.XmlSerializer> klasy, który serializuje tylko pola publiczne. Aby uzyskać informacje dotyczące wykluczania zmienne elementu członkowskiego z serializacji binarnej, zobacz [serializacja selektywna](selective-serialization.md).  
  
Przywracanie poprzedni stan obiektu jest równie proste. Najpierw należy utworzyć strumień do odczytu i <xref:System.Runtime.Serialization.Formatter>, a następnie wydać polecenie program formatujący deserializacji obiektu. W poniższym przykładzie kodu pokazano, jak to zrobić.  
  
```csharp  
IFormatter formatter = new BinaryFormatter();  
Stream stream = new FileStream("MyFile.bin", FileMode.Open, FileAccess.Read, FileShare.Read);  
MyObject obj = (MyObject) formatter.Deserialize(stream);  
stream.Close();  
  
// Here's the proof.  
Console.WriteLine("n1: {0}", obj.n1);  
Console.WriteLine("n2: {0}", obj.n2);  
Console.WriteLine("str: {0}", obj.str);  
```  
  
<xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> Używane powyżej jest bardzo wydajny i tworzy strumień bajtów compact. Dla wszystkich obiektów z tego programu formatującego również może być zdeserializowany z nim, dzięki czemu idealne narzędzie serializacji obiektów, które zostanie przeprowadzona na programie .NET Framework. Należy pamiętać, że konstruktorów nie są wywoływane, gdy deserializowany jest obiekt. To ograniczenie jest umieszczany na deserializacji ze względu na wydajność. Jednak narusza niektórych zwykłym umów przez środowisko uruchomieniowe z modułu zapisywania obiektu i deweloperów należy upewnić się, że zrozumieć zagadnienia, kiedy oznaczanie jako możliwy do serializacji obiektu.  
  
Jeśli przenoszenia jest wymagany, użyj <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> zamiast tego. Po prostu zastąpić **elementu** w kodzie powyżej z **SoapFormatter,** i wywołać **Serialize** i **Deserialize** tak jak poprzednio. Ten program formatujący tworzy poniższe dane wyjściowe na przykład powyżej.  
  
```xml  
<SOAP-ENV:Envelope  
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"  
  xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
  xmlns:SOAP- ENC="http://schemas.xmlsoap.org/soap/encoding/"  
  xmlns:SOAP- ENV="http://schemas.xmlsoap.org/soap/envelope/"  
  SOAP-ENV:encodingStyle=  
  "http://schemas.microsoft.com/soap/encoding/clr/1.0"  
  "http://schemas.xmlsoap.org/soap/encoding/"  
  xmlns:a1="http://schemas.microsoft.com/clr/assem/ToFile">  
  
  <SOAP-ENV:Body>  
    <a1:MyObject id="ref-1">  
      <n1>1</n1>  
      <n2>24</n2>  
      <str id="ref-3">Some String</str>  
    </a1:MyObject>  
  </SOAP-ENV:Body>  
</SOAP-ENV:Envelope>  
```  
  
Ważne jest, aby pamiętać, że [Serializable](xref:System.SerializableAttribute) atrybutu nie może być dziedziczona. Jeśli klasa nowe z `MyObject`, Nowa klasa musi być oznaczona atrybutem także lub nie może być serializowany. Na przykład podczas próby serializacji wystąpienia klasy poniżej, otrzymasz <xref:System.Runtime.Serialization.SerializationException> informacją, że `MyStuff` typ nie jest oznaczony jako możliwy do serializacji.  
  
```csharp  
public class MyStuff : MyObject   
{  
  public int n3;  
}  
```  
  
 Za pomocą [Serializable](xref:System.SerializableAttribute) jest wygodne, ale ma ograniczenia wykazać, jak wcześniej. Zapoznaj się [wytyczne serializacji](serialization-guidelines.md) informacji o podczas należy oznaczyć klasę do serializacji. Nie można dodać serializacji do klasy, został skompilowany.  
  
## <a name="see-also"></a>Zobacz także

- [Serializacja binarna](binary-serialization.md)  
- [Serializacja XML i SOAP](xml-and-soap-serialization.md)
