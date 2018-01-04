---
title: Podstawowe serializacji
ms.date: 03/30/2017
ms.prod: .net
ms.topic: article
helpviewer_keywords:
- binary serialization, basic serialization
- serialization, basic serialization
ms.assetid: d899d43c-335a-433e-a589-cd187192984f
dev_langs: CSharp
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 822b05758c7751e6f82f7a7f46a219d2c0001cd1
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="basic-serialization"></a>Podstawowe serializacji

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

Najprostszym sposobem, aby klasę serializacji jest Oznacz go z <xref:System.SerializableAttribute> w następujący sposób.  
  
```csharp  
[Serializable]  
public class MyObject {  
  public int n1 = 0;  
  public int n2 = 0;  
  public String str = null;  
}  
```  
  
Poniższy przykład kodu pokazuje, jak wystąpienie tej klasy może być Zserializowany do pliku.  
  
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
  
W tym przykładzie używa binarne elementu formatującego do wykonywania serializacji. Wszystko co należy zrobić jest utworzenie wystąpienia strumienia i chcesz użyć, a następnie Wywołaj program formatujący **serializacja** metody w element formatujący. Strumień i do serializacji obiektu są dostarczane jako parametry do tego połączenia. Mimo że go nie jest jawnie prezentowana w tym przykładzie, wszystkie zmienne Członkowskie klasy będą wykonywane szeregowo — nawet zmienne oznaczony jako prywatny. W tym aspektem serializacji binarnej różni się od <xref:System.Xml.Serialization.XmlSerializer> klasy, która serializuje tylko pola publiczne. Aby uzyskać informacje na z wyłączeniem zmiennych Członkowskich z serializacji binarnej, zobacz [selektywnego serializacji](selective-serialization.md).  
  
Przywracanie poprzedni stan obiektu jest równie proste. Najpierw utwórz strumień do odczytu i <xref:System.Runtime.Serialization.Formatter>, a następnie poinstruować program formatujący deserializacji obiektu. W poniższym przykładzie kodu pokazano, jak to zrobić.  
  
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
  
<xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> Używane powyżej jest bardzo wydajny i tworzy strumień bajtów compact. Dla wszystkich obiektów z tego programu formatującego również może być zdeserializowany z nim, dzięki czemu idealne narzędzie serializacji obiektów, które zostanie przeprowadzona na programie .NET Framework. Należy pamiętać, że konstruktorów nie są wywoływane, gdy deserializowany jest obiekt. To ograniczenie jest umieszczona na deserializacji ze względu na wydajność. Jednak narusza niektórych zwykłym umów przez środowisko uruchomieniowe z modułu zapisywania obiektu i deweloperów należy upewnić się, że zrozumieć zagadnienia, kiedy oznaczanie jako możliwy do serializacji obiektu.  
  
Jeśli przenośność jest wymagane, użyj <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> zamiast tego. Po prostu zastąpić **elementu** w kodzie powyżej z **SoapFormatter,** i Wywołaj **serializacja** i **Deserialize** jak poprzednio. Ten program formatujący tworzy następujące dane wyjściowe, na przykład użyć powyżej.  
  
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
  
Należy zauważyć, że [Serializable](xref:System.SerializableAttribute) atrybutu nie może być dziedziczona. Jeśli klasa nowe z `MyObject`, Nowa klasa musi być oznaczona atrybutem także lub nie może być serializowany. Na przykład przy próbie serializacji wystąpienia klasy poniżej, otrzymasz <xref:System.Runtime.Serialization.SerializationException> informujące, że `MyStuff` typ nie jest oznaczony jako możliwy do serializacji.  
  
```csharp  
public class MyStuff : MyObject   
{  
  public int n3;  
}  
```  
  
 Przy użyciu [Serializable](xref:System.SerializableAttribute) atrybut jest wygodne, ale ma ograniczenia przedstawionej wcześniej. Zapoznaj się [wytyczne serializacji](serialization-guidelines.md) informacji o kiedy należy oznaczyć klasę dla serializacji. Nie można dodać serializacji do klasy, został skompilowany.  
  
## <a name="see-also"></a>Zobacz także  
 [Serializacja binarna](binary-serialization.md)  
 [Serializacja XML i SOAP](xml-and-soap-serialization.md)
