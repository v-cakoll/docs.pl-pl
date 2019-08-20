---
title: 'Instrukcje: Odczytaj dane obiektu z pliku XML (C#)'
ms.date: 07/20/2015
ms.assetid: 6ad60d96-a4d9-48e6-a8b0-d7f6f803cafa
ms.openlocfilehash: 1d6ec71b9e408e1536063fc3d8f1badc0f38551e
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69590742"
---
# <a name="how-to-read-object-data-from-an-xml-file-c"></a><span data-ttu-id="2531a-102">Instrukcje: Odczytaj dane obiektu z pliku XML (C#)</span><span class="sxs-lookup"><span data-stu-id="2531a-102">How to: Read Object Data from an XML File (C#)</span></span>
<span data-ttu-id="2531a-103">Ten przykład odczytuje dane obiektu, które wcześniej Zapisano do pliku XML przy użyciu <xref:System.Xml.Serialization.XmlSerializer> klasy.</span><span class="sxs-lookup"><span data-stu-id="2531a-103">This example reads object data that was previously written to an XML file using the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2531a-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="2531a-104">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="2531a-105">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="2531a-105">Compiling the Code</span></span>  
 <span data-ttu-id="2531a-106">Zastąp nazwę pliku "c:\temp\SerializationOverview.xml" nazwą pliku zawierającego serializowane dane.</span><span class="sxs-lookup"><span data-stu-id="2531a-106">Replace the file name "c:\temp\SerializationOverview.xml" with the name of the file containing the serialized data.</span></span> <span data-ttu-id="2531a-107">Aby uzyskać więcej informacji na temat serializowania danych [, zobacz How to: Zapisz dane obiektu w pliku XML (C#).](./how-to-write-object-data-to-an-xml-file.md)</span><span class="sxs-lookup"><span data-stu-id="2531a-107">For more information about serializing data, see [How to: Write Object Data to an XML File (C#)](./how-to-write-object-data-to-an-xml-file.md).</span></span>  
  
 <span data-ttu-id="2531a-108">Klasa musi mieć Konstruktor publiczny bez parametrów.</span><span class="sxs-lookup"><span data-stu-id="2531a-108">The class must have a public constructor without parameters.</span></span>  
  
 <span data-ttu-id="2531a-109">Tylko publiczne właściwości i pola są deserializowane.</span><span class="sxs-lookup"><span data-stu-id="2531a-109">Only public properties and fields are deserialized.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="2531a-110">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="2531a-110">Robust Programming</span></span>  
 <span data-ttu-id="2531a-111">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="2531a-111">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="2531a-112">Serializowana Klasa nie ma publicznego konstruktora bez parametrów.</span><span class="sxs-lookup"><span data-stu-id="2531a-112">The class being serialized does not have a public, parameterless constructor.</span></span>  
  
- <span data-ttu-id="2531a-113">Dane w pliku nie reprezentują danych z klasy, która ma zostać poddana deserializacji.</span><span class="sxs-lookup"><span data-stu-id="2531a-113">The data in the file does not represent data from the class to be deserialized.</span></span>  
  
- <span data-ttu-id="2531a-114">Plik nie istnieje (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="2531a-114">The file does not exist (<xref:System.IO.IOException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="2531a-115">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="2531a-115">.NET Framework Security</span></span>  
 <span data-ttu-id="2531a-116">Zawsze Weryfikuj dane wejściowe i nigdy nie wykonuj deserializacji danych z niezaufanego źródła.</span><span class="sxs-lookup"><span data-stu-id="2531a-116">Always verify inputs, and never deserialize data from an untrusted source.</span></span> <span data-ttu-id="2531a-117">Nowo utworzony obiekt jest uruchamiany na komputerze lokalnym z uprawnieniami kodu, który został deserializowany.</span><span class="sxs-lookup"><span data-stu-id="2531a-117">The re-created object runs on a local computer with the permissions of the code that deserialized it.</span></span> <span data-ttu-id="2531a-118">Sprawdź wszystkie dane wejściowe, zanim użyjesz danych w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="2531a-118">Verify all inputs before using the data in your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2531a-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2531a-119">See also</span></span>

- <xref:System.IO.StreamWriter>
- [<span data-ttu-id="2531a-120">Instrukcje: Zapisz dane obiektu w pliku XML (C#)</span><span class="sxs-lookup"><span data-stu-id="2531a-120">How to: Write Object Data to an XML File (C#)</span></span>](./how-to-write-object-data-to-an-xml-file.md)
- [<span data-ttu-id="2531a-121">Serializacja (C#)</span><span class="sxs-lookup"><span data-stu-id="2531a-121">Serialization (C#)</span></span>](./index.md)
- [<span data-ttu-id="2531a-122">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="2531a-122">C# Programming Guide</span></span>](../../index.md)
