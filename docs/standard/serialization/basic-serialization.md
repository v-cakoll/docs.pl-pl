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
# <a name="basic-serialization"></a><span data-ttu-id="a9ac8-103">Serializacja podstawowa</span><span class="sxs-lookup"><span data-stu-id="a9ac8-103">Basic serialization</span></span>

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

<span data-ttu-id="a9ac8-104">Najprostszym sposobem, aby można było serializować klasę, jest oznaczenie jej w <xref:System.SerializableAttribute> następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="a9ac8-104">The easiest way to make a class serializable is to mark it with the <xref:System.SerializableAttribute> as follows.</span></span>  
  
```csharp  
[Serializable]  
public class MyObject {  
  public int n1 = 0;  
  public int n2 = 0;  
  public String str = null;  
}  
```  
  
<span data-ttu-id="a9ac8-105">Poniższy przykład kodu pokazuje, jak wystąpienie tej klasy może być serializowane do pliku.</span><span class="sxs-lookup"><span data-stu-id="a9ac8-105">The following code example shows how an instance of this class can be serialized to a file.</span></span>  
  
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
  
<span data-ttu-id="a9ac8-106">W tym przykładzie zastosowano binarny plik formatujący do serializacji.</span><span class="sxs-lookup"><span data-stu-id="a9ac8-106">This example uses a binary formatter to do the serialization.</span></span> <span data-ttu-id="a9ac8-107">Wszystko, co należy zrobić, to utworzenie wystąpienia strumienia i programu formatującego, którego zamierzasz użyć, a następnie Wywołaj metodę **serializacji** w programie formatującego.</span><span class="sxs-lookup"><span data-stu-id="a9ac8-107">All you need to do is create an instance of the stream and the formatter you intend to use, and then call the **Serialize** method on the formatter.</span></span> <span data-ttu-id="a9ac8-108">Strumień i do serializacji obiektu są dostarczane jako parametry do tego połączenia.</span><span class="sxs-lookup"><span data-stu-id="a9ac8-108">The stream and the object to serialize are provided as parameters to this call.</span></span> <span data-ttu-id="a9ac8-109">Chociaż nie jest to jawnie zademonstrowane w tym przykładzie, wszystkie zmienne składowe klasy będą serializowane — nawet zmienne oznaczone jako prywatne.</span><span class="sxs-lookup"><span data-stu-id="a9ac8-109">Although it is not explicitly demonstrated in this example, all member variables of a class will be serialized—even variables marked as private.</span></span> <span data-ttu-id="a9ac8-110">W tym aspekcie Serializacja binarna różni się od <xref:System.Xml.Serialization.XmlSerializer> klasy, która tylko serializować pola publiczne.</span><span class="sxs-lookup"><span data-stu-id="a9ac8-110">In this aspect, binary serialization differs from the <xref:System.Xml.Serialization.XmlSerializer> class, which only serializes public fields.</span></span> <span data-ttu-id="a9ac8-111">Aby uzyskać informacje na temat wykluczania zmiennych członkowskich z serializacji binarnej, zobacz [selektywne serializacji](selective-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="a9ac8-111">For information on excluding member variables from binary serialization, see [Selective Serialization](selective-serialization.md).</span></span>  
  
<span data-ttu-id="a9ac8-112">Przywracanie poprzedni stan obiektu jest równie proste.</span><span class="sxs-lookup"><span data-stu-id="a9ac8-112">Restoring the object back to its former state is just as easy.</span></span> <span data-ttu-id="a9ac8-113">Najpierw utwórz strumień do odczytu i a <xref:System.Runtime.Serialization.Formatter> , a następnie nakazuje programowi formatującego deserializacji obiektu.</span><span class="sxs-lookup"><span data-stu-id="a9ac8-113">First, create a stream for reading and a <xref:System.Runtime.Serialization.Formatter>, and then instruct the formatter to deserialize the object.</span></span> <span data-ttu-id="a9ac8-114">W poniższym przykładzie kodu pokazano, jak to zrobić.</span><span class="sxs-lookup"><span data-stu-id="a9ac8-114">The code example below shows how this is done.</span></span>  
  
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
  
<span data-ttu-id="a9ac8-115"><xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>Użyte powyżej jest bardzo wydajne i tworzy strumień bajtów kompaktowych.</span><span class="sxs-lookup"><span data-stu-id="a9ac8-115">The <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> used above is very efficient and produces a compact byte stream.</span></span> <span data-ttu-id="a9ac8-116">Dla wszystkich obiektów z tego programu formatującego również może być zdeserializowany z nim, dzięki czemu idealne narzędzie serializacji obiektów, które zostanie przeprowadzona na programie .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a9ac8-116">All objects serialized with this formatter can also be deserialized with it, which makes it an ideal tool for serializing objects that will be deserialized on the .NET Framework.</span></span> <span data-ttu-id="a9ac8-117">Należy pamiętać, że konstruktorów nie są wywoływane, gdy deserializowany jest obiekt.</span><span class="sxs-lookup"><span data-stu-id="a9ac8-117">It is important to note that constructors are not called when an object is deserialized.</span></span> <span data-ttu-id="a9ac8-118">To ograniczenie jest umieszczane na deserializacji ze względu na wydajność.</span><span class="sxs-lookup"><span data-stu-id="a9ac8-118">This constraint is placed on deserialization for performance reasons.</span></span> <span data-ttu-id="a9ac8-119">Jednak narusza niektórych zwykłym umów przez środowisko uruchomieniowe z modułu zapisywania obiektu i deweloperów należy upewnić się, że zrozumieć zagadnienia, kiedy oznaczanie jako możliwy do serializacji obiektu.</span><span class="sxs-lookup"><span data-stu-id="a9ac8-119">However, this violates some of the usual contracts the runtime makes with the object writer, and developers should ensure that they understand the ramifications when marking an object as serializable.</span></span>  
  
<span data-ttu-id="a9ac8-120">Jeśli przenośność jest wymagana, użyj <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> zamiast niego.</span><span class="sxs-lookup"><span data-stu-id="a9ac8-120">If portability is a requirement, use the <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> instead.</span></span> <span data-ttu-id="a9ac8-121">Po prostu Zastąp **BinaryFormatter** w powyższym kodzie z **SoapFormatter,** a następnie Wywołaj **Serializacja** i **deserializacja** jako poprzednio.</span><span class="sxs-lookup"><span data-stu-id="a9ac8-121">Simply replace the **BinaryFormatter** in the code above with **SoapFormatter,** and call **Serialize** and **Deserialize** as before.</span></span> <span data-ttu-id="a9ac8-122">Ten program formatujący tworzy następujące dane wyjściowe dla przykładu użytego powyżej.</span><span class="sxs-lookup"><span data-stu-id="a9ac8-122">This formatter produces the following output for the example used above.</span></span>  
  
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
  
<span data-ttu-id="a9ac8-123">Należy pamiętać, że atrybut możliwy do [serializacji](xref:System.SerializableAttribute) nie może być dziedziczony.</span><span class="sxs-lookup"><span data-stu-id="a9ac8-123">It's important to note that the [Serializable](xref:System.SerializableAttribute) attribute cannot be inherited.</span></span> <span data-ttu-id="a9ac8-124">Jeśli klasa nowe z `MyObject`, Nowa klasa musi być oznaczona atrybutem także lub nie może być serializowany.</span><span class="sxs-lookup"><span data-stu-id="a9ac8-124">If you derive a new class from `MyObject`, the new class must be marked with the attribute as well, or it cannot be serialized.</span></span> <span data-ttu-id="a9ac8-125">Na przykład podczas próby serializacji wystąpienia klasy poniżej zostanie wyświetlony komunikat <xref:System.Runtime.Serialization.SerializationException> informujący o tym, że `MyStuff` Typ nie jest oznaczony jako możliwy do serializacji.</span><span class="sxs-lookup"><span data-stu-id="a9ac8-125">For example, when you attempt to serialize an instance of the class below, you'll get a <xref:System.Runtime.Serialization.SerializationException> informing you that the `MyStuff` type is not marked as serializable.</span></span>  
  
```csharp  
public class MyStuff : MyObject
{  
  public int n3;  
}  
```  
  
 <span data-ttu-id="a9ac8-126">Użycie atrybutu [Serializable](xref:System.SerializableAttribute) jest wygodne, ale ma ograniczenia, jak poprzednio pokazano.</span><span class="sxs-lookup"><span data-stu-id="a9ac8-126">Using the [Serializable](xref:System.SerializableAttribute) attribute is convenient, but it has limitations as previously demonstrated.</span></span> <span data-ttu-id="a9ac8-127">Zapoznaj się z [wytycznymi serializacji](serialization-guidelines.md) , aby uzyskać informacje o tym, kiedy należy oznaczyć klasę do serializacji.</span><span class="sxs-lookup"><span data-stu-id="a9ac8-127">Refer to the [Serialization Guidelines](serialization-guidelines.md) for information about when you should mark a class for serialization.</span></span> <span data-ttu-id="a9ac8-128">Serializacja nie może zostać dodana do klasy, gdy została skompilowana.</span><span class="sxs-lookup"><span data-stu-id="a9ac8-128">Serialization cannot be added to a class after it has been compiled.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9ac8-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a9ac8-129">See also</span></span>

- [<span data-ttu-id="a9ac8-130">Serializacja binarna</span><span class="sxs-lookup"><span data-stu-id="a9ac8-130">Binary Serialization</span></span>](binary-serialization.md)
- [<span data-ttu-id="a9ac8-131">Serializacja XML i SOAP</span><span class="sxs-lookup"><span data-stu-id="a9ac8-131">XML and SOAP Serialization</span></span>](xml-and-soap-serialization.md)
