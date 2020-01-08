---
title: Jak napisać dane obiektu do pliku XML (C#)
ms.date: 07/20/2015
ms.assetid: 7681eb98-703d-4005-a369-26a7bca0f894
ms.openlocfilehash: 475e9398f20a2a4db9fb537d0b8d44f0273e980b
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346448"
---
# <a name="how-to-write-object-data-to-an-xml-file-c"></a><span data-ttu-id="e424b-102">Jak napisać dane obiektu do pliku XML (C#)</span><span class="sxs-lookup"><span data-stu-id="e424b-102">How to write object data to an XML file (C#)</span></span>
<span data-ttu-id="e424b-103">Ten przykład zapisuje obiekt z klasy do pliku XML przy użyciu klasy <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="e424b-103">This example writes the object from a class to an XML file using the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e424b-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="e424b-104">Example</span></span>  
  
```csharp  
public class XMLWrite  
{  
  
   static void Main(string[] args)  
    {  
        WriteXML();  
    }  
  
    public class Book  
    {  
        public String title;   
    }  
  
    public static void WriteXML()  
    {  
        Book overview = new Book();  
        overview.title = "Serialization Overview";  
        System.Xml.Serialization.XmlSerializer writer =   
            new System.Xml.Serialization.XmlSerializer(typeof(Book));  
  
        var path = Environment.GetFolderPath(Environment.SpecialFolder.MyDocuments) + "//SerializationOverview.xml";  
        System.IO.FileStream file = System.IO.File.Create(path);  
  
        writer.Serialize(file, overview);  
        file.Close();  
    }  
}  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e424b-105">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="e424b-105">Compiling the Code</span></span>  
 <span data-ttu-id="e424b-106">Serializacja klasy musi mieć Konstruktor publiczny bez parametrów.</span><span class="sxs-lookup"><span data-stu-id="e424b-106">The class being serialized must have a public constructor without parameters.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="e424b-107">Skuteczne programowanie</span><span class="sxs-lookup"><span data-stu-id="e424b-107">Robust Programming</span></span>  
 <span data-ttu-id="e424b-108">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="e424b-108">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="e424b-109">Serializowana Klasa nie ma publicznego konstruktora bez parametrów.</span><span class="sxs-lookup"><span data-stu-id="e424b-109">The class being serialized does not have a public, parameterless constructor.</span></span>  
  
- <span data-ttu-id="e424b-110">Plik istnieje i jest tylko do odczytu (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="e424b-110">The file exists and is read-only (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="e424b-111">Ścieżka jest za długa (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="e424b-111">The path is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="e424b-112">Dysk jest pełny (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="e424b-112">The disk is full (<xref:System.IO.IOException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="e424b-113">Zabezpieczenia programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="e424b-113">.NET Framework Security</span></span>  
 <span data-ttu-id="e424b-114">Ten przykład tworzy nowy plik, jeśli plik jeszcze nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="e424b-114">This example creates a new file, if the file does not already exist.</span></span> <span data-ttu-id="e424b-115">Jeśli aplikacja musi utworzyć plik, ta aplikacja wymaga `Create` dostępu do folderu.</span><span class="sxs-lookup"><span data-stu-id="e424b-115">If an application needs to create a file, that application needs `Create` access for the folder.</span></span> <span data-ttu-id="e424b-116">Jeśli plik już istnieje, aplikacja wymaga tylko `Write` dostępu, ale ma mniejsze uprawnienia.</span><span class="sxs-lookup"><span data-stu-id="e424b-116">If the file already exists, the application needs only `Write` access, a lesser privilege.</span></span> <span data-ttu-id="e424b-117">Jeśli to możliwe, bezpieczniejsze jest tworzenie plików podczas wdrażania i udzielanie `Read` dostęp do pojedynczego pliku, a nie `Create` dostępu do folderu.</span><span class="sxs-lookup"><span data-stu-id="e424b-117">Where possible, it is more secure to create the file during deployment, and only grant `Read` access to a single file, rather than `Create` access for a folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e424b-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e424b-118">See also</span></span>

- <xref:System.IO.StreamWriter>
- [<span data-ttu-id="e424b-119">Jak odczytać dane obiektu z pliku XML (C#)</span><span class="sxs-lookup"><span data-stu-id="e424b-119">How to read object data from an XML file (C#)</span></span>](./how-to-read-object-data-from-an-xml-file.md)
- [<span data-ttu-id="e424b-120">Serializacja (C#)</span><span class="sxs-lookup"><span data-stu-id="e424b-120">Serialization (C#)</span></span>](./index.md)
