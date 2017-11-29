---
title: 'Porady: odczytywanie danych o obiektach z pliku XML (C#)'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 6ad60d96-a4d9-48e6-a8b0-d7f6f803cafa
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 6a3389de2f3272a546a7380ef386f5d88666e6d1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-read-object-data-from-an-xml-file-c"></a><span data-ttu-id="d26c7-102">Porady: odczytywanie danych o obiektach z pliku XML (C#)</span><span class="sxs-lookup"><span data-stu-id="d26c7-102">How to: Read Object Data from an XML File (C#)</span></span>
<span data-ttu-id="d26c7-103">Ten przykład odczytuje danych obiektów, które zostały wcześniej zapisane do pliku XML przy użyciu <xref:System.Xml.Serialization.XmlSerializer> klasy.</span><span class="sxs-lookup"><span data-stu-id="d26c7-103">This example reads object data that was previously written to an XML file using the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d26c7-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="d26c7-104">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="d26c7-105">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="d26c7-105">Compiling the Code</span></span>  
 <span data-ttu-id="d26c7-106">Zamień na nazwę pliku zawierającego dane serializowane nazwa pliku "c:\temp\SerializationOverview.xml".</span><span class="sxs-lookup"><span data-stu-id="d26c7-106">Replace the file name "c:\temp\SerializationOverview.xml" with the name of the file containing the serialized data.</span></span> <span data-ttu-id="d26c7-107">Aby uzyskać więcej informacji na temat serializacja danych, zobacz [porady: zapis danych obiektów do pliku XML (C#)](../../../../csharp/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md).</span><span class="sxs-lookup"><span data-stu-id="d26c7-107">For more information about serializing data, see [How to: Write Object Data to an XML File (C#)](../../../../csharp/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md).</span></span>  
  
 <span data-ttu-id="d26c7-108">Klasa musi mieć publicznego konstruktora bez parametrów.</span><span class="sxs-lookup"><span data-stu-id="d26c7-108">The class must have a public constructor without parameters.</span></span>  
  
 <span data-ttu-id="d26c7-109">Rozszeregować są tylko właściwości publiczne i pola.</span><span class="sxs-lookup"><span data-stu-id="d26c7-109">Only public properties and fields are deserialized.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="d26c7-110">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="d26c7-110">Robust Programming</span></span>  
 <span data-ttu-id="d26c7-111">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="d26c7-111">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="d26c7-112">Klasa poddany serializacji ma publicznego konstruktora bez parametrów.</span><span class="sxs-lookup"><span data-stu-id="d26c7-112">The class being serialized does not have a public, parameterless constructor.</span></span>  
  
-   <span data-ttu-id="d26c7-113">Dane w pliku nie reprezentuje dane z klasy do zdeserializowania.</span><span class="sxs-lookup"><span data-stu-id="d26c7-113">The data in the file does not represent data from the class to be deserialized.</span></span>  
  
-   <span data-ttu-id="d26c7-114">Plik nie istnieje (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="d26c7-114">The file does not exist (<xref:System.IO.IOException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="d26c7-115">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="d26c7-115">.NET Framework Security</span></span>  
 <span data-ttu-id="d26c7-116">Zawsze Sprawdź dane wejściowe i nigdy nie deserializować danych z niezaufanego źródła.</span><span class="sxs-lookup"><span data-stu-id="d26c7-116">Always verify inputs, and never deserialize data from an untrusted source.</span></span> <span data-ttu-id="d26c7-117">Uruchamia ponownie utworzyć obiekt na komputerze lokalnym przy użyciu uprawnień kodu, który go deserializacji.</span><span class="sxs-lookup"><span data-stu-id="d26c7-117">The re-created object runs on a local computer with the permissions of the code that deserialized it.</span></span> <span data-ttu-id="d26c7-118">Sprawdź wszystkie dane wejściowe, zanim użyjesz danych w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d26c7-118">Verify all inputs before using the data in your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d26c7-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d26c7-119">See Also</span></span>  
 <xref:System.IO.StreamWriter>  
 [<span data-ttu-id="d26c7-120">Porady: wpisywanie danych o obiektach do pliku XML (C#)</span><span class="sxs-lookup"><span data-stu-id="d26c7-120">How to: Write Object Data to an XML File (C#)</span></span>](../../../../csharp/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md)  
 [<span data-ttu-id="d26c7-121">Serializacja (C#)</span><span class="sxs-lookup"><span data-stu-id="d26c7-121">Serialization (C# )</span></span>](../../../../csharp/programming-guide/concepts/serialization/index.md)  
 [<span data-ttu-id="d26c7-122">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="d26c7-122">C# Programming Guide</span></span>](../../../../csharp/programming-guide/index.md)
