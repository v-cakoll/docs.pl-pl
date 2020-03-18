---
title: Jak odczytywać dane obiektu z pliku XML (C#)
ms.date: 07/20/2015
ms.assetid: 6ad60d96-a4d9-48e6-a8b0-d7f6f803cafa
ms.openlocfilehash: 18428cbe2f2d3b9434a77ee4d063ceabbba6bcb8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79167821"
---
# <a name="how-to-read-object-data-from-an-xml-file-c"></a><span data-ttu-id="9d80a-102">Jak odczytywać dane obiektu z pliku XML (C#)</span><span class="sxs-lookup"><span data-stu-id="9d80a-102">How to read object data from an XML file (C#)</span></span>
<span data-ttu-id="9d80a-103">W tym przykładzie odczytuje dane obiektu, który <xref:System.Xml.Serialization.XmlSerializer> został wcześniej zapisany do pliku XML przy użyciu klasy.</span><span class="sxs-lookup"><span data-stu-id="9d80a-103">This example reads object data that was previously written to an XML file using the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9d80a-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="9d80a-104">Example</span></span>  
  
```csharp  
public class Book  
{  
    public String title;  
}
  
public void ReadXML()  
{  
    // First write something so that there is something to read ...  
    var b = new Book { title = "Serialization Overview" };  
    var writer = new System.Xml.Serialization.XmlSerializer(typeof(Book));  
    var wfile = new System.IO.StreamWriter(@"c:\temp\SerializationOverview.xml");  
    writer.Serialize(wfile, b);  
    wfile.Close();  
  
    // Now we can read the serialized book ...  
    System.Xml.Serialization.XmlSerializer reader =
        new System.Xml.Serialization.XmlSerializer(typeof(Book));  
    System.IO.StreamReader file = new System.IO.StreamReader(  
        @"c:\temp\SerializationOverview.xml");  
    Book overview =  (Book)reader.Deserialize(file);  
    file.Close();  
  
    Console.WriteLine(overview.title);  
  
}  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9d80a-105">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="9d80a-105">Compiling the Code</span></span>  
<span data-ttu-id="9d80a-106">Zastąp nazwę pliku "c:\temp\SerializationOverview.xml" nazwą pliku zawierającego dane serializowane.</span><span class="sxs-lookup"><span data-stu-id="9d80a-106">Replace the file name "c:\temp\SerializationOverview.xml" with the name of the file containing the serialized data.</span></span> <span data-ttu-id="9d80a-107">Aby uzyskać więcej informacji na temat serializacji danych, zobacz [Jak zapisywać dane obiektów w pliku XML (C#).](./how-to-write-object-data-to-an-xml-file.md)</span><span class="sxs-lookup"><span data-stu-id="9d80a-107">For more information about serializing data, see [How to write object data to an XML file (C#)](./how-to-write-object-data-to-an-xml-file.md).</span></span>
  
 <span data-ttu-id="9d80a-108">Klasa musi mieć konstruktora publicznego bez parametrów.</span><span class="sxs-lookup"><span data-stu-id="9d80a-108">The class must have a public constructor without parameters.</span></span>  
  
 <span data-ttu-id="9d80a-109">Deserializowane są tylko właściwości i pola publiczne.</span><span class="sxs-lookup"><span data-stu-id="9d80a-109">Only public properties and fields are deserialized.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="9d80a-110">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="9d80a-110">Robust Programming</span></span>  
 <span data-ttu-id="9d80a-111">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="9d80a-111">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="9d80a-112">Klasa serializacji nie ma konstruktora publicznego, bezparametrów.</span><span class="sxs-lookup"><span data-stu-id="9d80a-112">The class being serialized does not have a public, parameterless constructor.</span></span>  
  
- <span data-ttu-id="9d80a-113">Dane w pliku nie reprezentują danych z klasy, która ma zostać zdeserializowana.</span><span class="sxs-lookup"><span data-stu-id="9d80a-113">The data in the file does not represent data from the class to be deserialized.</span></span>  
  
- <span data-ttu-id="9d80a-114">Plik nie istnieje<xref:System.IO.IOException>( ).</span><span class="sxs-lookup"><span data-stu-id="9d80a-114">The file does not exist (<xref:System.IO.IOException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="9d80a-115">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="9d80a-115">.NET Framework Security</span></span>  
 <span data-ttu-id="9d80a-116">Zawsze sprawdzaj dane wejściowe i nigdy nie deserializuj danych z niezaufanego źródła.</span><span class="sxs-lookup"><span data-stu-id="9d80a-116">Always verify inputs, and never deserialize data from an untrusted source.</span></span> <span data-ttu-id="9d80a-117">Ponownie utworzony obiekt jest uruchamiany na komputerze lokalnym z uprawnieniami kodu, który go deserializował.</span><span class="sxs-lookup"><span data-stu-id="9d80a-117">The re-created object runs on a local computer with the permissions of the code that deserialized it.</span></span> <span data-ttu-id="9d80a-118">Sprawdź wszystkie dane wejściowe, zanim użyjesz danych w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9d80a-118">Verify all inputs before using the data in your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d80a-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9d80a-119">See also</span></span>

- <xref:System.IO.StreamWriter>
- [<span data-ttu-id="9d80a-120">Jak zapisywać dane obiektu do pliku XML (C#)</span><span class="sxs-lookup"><span data-stu-id="9d80a-120">How to write object data to an XML file (C#)</span></span>](./how-to-write-object-data-to-an-xml-file.md)
- [<span data-ttu-id="9d80a-121">Serializacja (C#)</span><span class="sxs-lookup"><span data-stu-id="9d80a-121">Serialization (C#)</span></span>](./index.md)
- [<span data-ttu-id="9d80a-122">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="9d80a-122">C# Programming Guide</span></span>](../../index.md)
