---
title: 'Instrukcje: Odczytywanie danych o obiektach z pliku XML (C#)'
ms.date: 07/20/2015
ms.assetid: 6ad60d96-a4d9-48e6-a8b0-d7f6f803cafa
ms.openlocfilehash: 33e4395c2be421385948d256a989d06ac215c9c4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61711100"
---
# <a name="how-to-read-object-data-from-an-xml-file-c"></a><span data-ttu-id="8a51c-102">Instrukcje: Odczytywanie danych o obiektach z pliku XML (C#)</span><span class="sxs-lookup"><span data-stu-id="8a51c-102">How to: Read Object Data from an XML File (C#)</span></span>
<span data-ttu-id="8a51c-103">W tym przykładzie odczytuje dane obiektów, które zostały wcześniej zapisane do pliku XML przy użyciu <xref:System.Xml.Serialization.XmlSerializer> klasy.</span><span class="sxs-lookup"><span data-stu-id="8a51c-103">This example reads object data that was previously written to an XML file using the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8a51c-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="8a51c-104">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="8a51c-105">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="8a51c-105">Compiling the Code</span></span>  
 <span data-ttu-id="8a51c-106">Nazwa pliku "c:\temp\SerializationOverview.xml" należy zastąpić nazwę pliku zawierającego dane serializowane.</span><span class="sxs-lookup"><span data-stu-id="8a51c-106">Replace the file name "c:\temp\SerializationOverview.xml" with the name of the file containing the serialized data.</span></span> <span data-ttu-id="8a51c-107">Aby uzyskać więcej informacji na temat serializowania danych zobacz [jak: Zapisywania obiektów danych do pliku XML (C#)](../../../../csharp/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md).</span><span class="sxs-lookup"><span data-stu-id="8a51c-107">For more information about serializing data, see [How to: Write Object Data to an XML File (C#)](../../../../csharp/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md).</span></span>  
  
 <span data-ttu-id="8a51c-108">Klasa musi mieć publicznego konstruktora bez parametrów.</span><span class="sxs-lookup"><span data-stu-id="8a51c-108">The class must have a public constructor without parameters.</span></span>  
  
 <span data-ttu-id="8a51c-109">Tylko właściwości publiczne i pola są deserializacji.</span><span class="sxs-lookup"><span data-stu-id="8a51c-109">Only public properties and fields are deserialized.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="8a51c-110">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="8a51c-110">Robust Programming</span></span>  
 <span data-ttu-id="8a51c-111">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="8a51c-111">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="8a51c-112">Klasa jest serializowana, nie ma publiczny konstruktor bez parametrów.</span><span class="sxs-lookup"><span data-stu-id="8a51c-112">The class being serialized does not have a public, parameterless constructor.</span></span>  
  
- <span data-ttu-id="8a51c-113">Dane w pliku nie reprezentuje dane z klasy, która ma zostać przeprowadzona.</span><span class="sxs-lookup"><span data-stu-id="8a51c-113">The data in the file does not represent data from the class to be deserialized.</span></span>  
  
- <span data-ttu-id="8a51c-114">Plik nie istnieje (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="8a51c-114">The file does not exist (<xref:System.IO.IOException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="8a51c-115">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="8a51c-115">.NET Framework Security</span></span>  
 <span data-ttu-id="8a51c-116">Zawsze sprawdzić dane wejściowe i nigdy nie deserializowanie danych z niezaufanego źródła.</span><span class="sxs-lookup"><span data-stu-id="8a51c-116">Always verify inputs, and never deserialize data from an untrusted source.</span></span> <span data-ttu-id="8a51c-117">Ponownie utworzyć obiekt działa na komputerze lokalnym z uprawnieniami kod, który deserializacji go.</span><span class="sxs-lookup"><span data-stu-id="8a51c-117">The re-created object runs on a local computer with the permissions of the code that deserialized it.</span></span> <span data-ttu-id="8a51c-118">Sprawdź wszystkie dane wejściowe, zanim użyjesz danych w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8a51c-118">Verify all inputs before using the data in your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a51c-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8a51c-119">See also</span></span>

- <xref:System.IO.StreamWriter>
- [<span data-ttu-id="8a51c-120">Instrukcje: Zapisywania obiektów danych do pliku XML (C#)</span><span class="sxs-lookup"><span data-stu-id="8a51c-120">How to: Write Object Data to an XML File (C#)</span></span>](../../../../csharp/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md)
- [<span data-ttu-id="8a51c-121">Serializacja (C#)</span><span class="sxs-lookup"><span data-stu-id="8a51c-121">Serialization (C#)</span></span>](../../../../csharp/programming-guide/concepts/serialization/index.md)
- [<span data-ttu-id="8a51c-122">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="8a51c-122">C# Programming Guide</span></span>](../../../../csharp/programming-guide/index.md)
