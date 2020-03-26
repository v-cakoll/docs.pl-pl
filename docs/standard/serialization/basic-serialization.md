---
title: Podstawowa serializacja
ms.date: 03/30/2017
helpviewer_keywords:
- binary serialization, basic serialization
- serialization, basic serialization
ms.assetid: d899d43c-335a-433e-a589-cd187192984f
dev_langs:
- CSharp
ms.openlocfilehash: ce86f7897c5c117c4fd6f1eabc4c8b802103261c
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2020
ms.locfileid: "80248033"
---
# <a name="basic-serialization"></a>Podstawowa serializacja

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

Najprostszym sposobem, aby klasa serializable jest oznaczyć go w <xref:System.SerializableAttribute> następujący sposób.  
  
```csharp  
[Serializable]  
public class MyObject {  
  public int n1 = 0;  
  public int n2 = 0;  
  public String str = null;  
}  
```  
  
Poniższy przykład kodu pokazuje, jak wystąpienie tej klasy może być serializowane do pliku.  
  
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
  
W tym przykładzie użyto formatera binarnego do serializacji. Wszystko, co musisz zrobić, to utworzyć wystąpienie strumienia i formatera, którego zamierzasz użyć, a następnie **wywołać metodę Serialize** na programie formatu. Strumień i do serializacji obiektu są dostarczane jako parametry do tego połączenia. Chociaż nie jest jawnie wykazane w tym przykładzie, wszystkie zmienne członkowskie klasy będą serializowane, nawet zmienne oznaczone jako prywatne. W tym aspekcie serializacji <xref:System.Xml.Serialization.XmlSerializer> binarnej różni się od klasy, która tylko serializuje pola publiczne. Aby uzyskać informacje na temat wykluczania zmiennych członkowskich z serializacji binarnej, zobacz [Serializacja selektywna](selective-serialization.md).  
  
Przywracanie poprzedni stan obiektu jest równie proste. Najpierw utwórz strumień do <xref:System.Runtime.Serialization.Formatter>odczytu i , a następnie poinstruuj formatera, aby deserializacji obiektu. Poniższy przykład kodu pokazuje, jak to zrobić.  
  
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
  
Zastosowane <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> powyżej jest bardzo wydajne i wytwarza kompaktowy strumień bajtów. Dla wszystkich obiektów z tego programu formatującego również może być zdeserializowany z nim, dzięki czemu idealne narzędzie serializacji obiektów, które zostanie przeprowadzona na programie .NET Framework. Należy pamiętać, że konstruktorów nie są wywoływane, gdy deserializowany jest obiekt. To ograniczenie jest umieszczane na deserializacji ze względu na wydajność. Jednak narusza niektórych zwykłym umów przez środowisko uruchomieniowe z modułu zapisywania obiektu i deweloperów należy upewnić się, że zrozumieć zagadnienia, kiedy oznaczanie jako możliwy do serializacji obiektu.  
  
Jeśli przenośność jest wymagana, <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> użyj zamiast tego. Wystarczy zastąpić **BinaryFormatter** w kodzie powyżej **soapformatter** i **wywołać Serialize** i **Deserialize** jak poprzednio. Ten formater tworzy następujące dane wyjściowe dla przykładu użytego powyżej.  
  
```xml  
<SOAP-ENV:Envelope  
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"  
  xmlns:xsd="http://www.w3.org/2001/XMLSchema"
  xmlns:SOAP-ENC="http://schemas.xmlsoap.org/soap/encoding/"  
  xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/"  
  SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/"  
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
  
Należy pamiętać, że nie można dziedziczyć atrybutu [Serializable.](xref:System.SerializableAttribute) Jeśli klasa nowe z `MyObject`, Nowa klasa musi być oznaczona atrybutem także lub nie może być serializowany. Na przykład podczas próby serializacji wystąpienia klasy poniżej, otrzymasz <xref:System.Runtime.Serialization.SerializationException> informację, `MyStuff` że typ nie jest oznaczony jako serializowalny.  
  
```csharp  
public class MyStuff : MyObject
{  
  public int n3;  
}  
```  
  
 Korzystanie z [atrybutu Serializable](xref:System.SerializableAttribute) jest wygodne, ale ma ograniczenia, jak wcześniej wykazano. Zapoznaj się z [wytycznymi serializacji,](serialization-guidelines.md) aby uzyskać informacje o tym, kiedy należy oznaczyć klasę do serializacji. Serializacji nie można dodać do klasy po jej skompilowaniu.  
  
## <a name="see-also"></a>Zobacz też

- [Serializacja binarna](binary-serialization.md)
- [Serializacja XML i SOAP](xml-and-soap-serialization.md)
