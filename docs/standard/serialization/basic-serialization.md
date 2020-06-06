---
title: Serializacja podstawowa
description: W tym artykule przedstawiono sposób serializacji klasy z SerializableAttribute i zawiera przykłady serializacji i deserializacji.
ms.date: 03/30/2017
helpviewer_keywords:
- binary serialization, basic serialization
- serialization, basic serialization
ms.assetid: d899d43c-335a-433e-a589-cd187192984f
dev_langs:
- CSharp
ms.openlocfilehash: 98ea6f23467b85dc270aa323e72a8a9b0934994a
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "83378430"
---
# <a name="basic-serialization"></a>Serializacja podstawowa

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

Najprostszym sposobem, aby można było serializować klasę, jest oznaczenie jej w <xref:System.SerializableAttribute> następujący sposób.  
  
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
  
W tym przykładzie zastosowano binarny plik formatujący do serializacji. Wszystko, co należy zrobić, to utworzenie wystąpienia strumienia i programu formatującego, którego zamierzasz użyć, a następnie Wywołaj metodę **serializacji** w programie formatującego. Strumień i do serializacji obiektu są dostarczane jako parametry do tego połączenia. Chociaż nie jest to jawnie zademonstrowane w tym przykładzie, wszystkie zmienne składowe klasy będą serializowane — nawet zmienne oznaczone jako prywatne. W tym aspekcie Serializacja binarna różni się od <xref:System.Xml.Serialization.XmlSerializer> klasy, która tylko serializować pola publiczne. Aby uzyskać informacje na temat wykluczania zmiennych członkowskich z serializacji binarnej, zobacz [selektywne serializacji](selective-serialization.md).  
  
Przywracanie poprzedni stan obiektu jest równie proste. Najpierw utwórz strumień do odczytu i a <xref:System.Runtime.Serialization.Formatter> , a następnie nakazuje programowi formatującego deserializacji obiektu. W poniższym przykładzie kodu pokazano, jak to zrobić.  
  
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
  
<xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>Użyte powyżej jest bardzo wydajne i tworzy strumień bajtów kompaktowych. Dla wszystkich obiektów z tego programu formatującego również może być zdeserializowany z nim, dzięki czemu idealne narzędzie serializacji obiektów, które zostanie przeprowadzona na programie .NET Framework. Należy pamiętać, że konstruktorów nie są wywoływane, gdy deserializowany jest obiekt. To ograniczenie jest umieszczane na deserializacji ze względu na wydajność. Jednak narusza niektórych zwykłym umów przez środowisko uruchomieniowe z modułu zapisywania obiektu i deweloperów należy upewnić się, że zrozumieć zagadnienia, kiedy oznaczanie jako możliwy do serializacji obiektu.  
  
Jeśli przenośność jest wymagana, użyj <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> zamiast niego. Po prostu Zastąp **BinaryFormatter** w powyższym kodzie z **SoapFormatter,** a następnie Wywołaj **Serializacja** i **deserializacja** jako poprzednio. Ten program formatujący tworzy następujące dane wyjściowe dla przykładu użytego powyżej.  
  
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
  
Należy pamiętać, że atrybut możliwy do [serializacji](xref:System.SerializableAttribute) nie może być dziedziczony. Jeśli klasa nowe z `MyObject`, Nowa klasa musi być oznaczona atrybutem także lub nie może być serializowany. Na przykład podczas próby serializacji wystąpienia klasy poniżej zostanie wyświetlony komunikat <xref:System.Runtime.Serialization.SerializationException> informujący o tym, że `MyStuff` Typ nie jest oznaczony jako możliwy do serializacji.  
  
```csharp  
public class MyStuff : MyObject
{  
  public int n3;  
}  
```  
  
 Użycie atrybutu [Serializable](xref:System.SerializableAttribute) jest wygodne, ale ma ograniczenia, jak poprzednio pokazano. Zapoznaj się z [wytycznymi serializacji](serialization-guidelines.md) , aby uzyskać informacje o tym, kiedy należy oznaczyć klasę do serializacji. Serializacja nie może zostać dodana do klasy, gdy została skompilowana.  
  
## <a name="see-also"></a>Zobacz także

- [Serializacja binarna](binary-serialization.md)
- [Serializacja XML i SOAP](xml-and-soap-serialization.md)
