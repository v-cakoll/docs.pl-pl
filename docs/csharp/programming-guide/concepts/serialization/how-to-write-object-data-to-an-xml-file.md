---
title: 'Porady: wpisywanie danych o obiektach do pliku XML (C#)'
ms.date: 07/20/2015
ms.assetid: 7681eb98-703d-4005-a369-26a7bca0f894
ms.openlocfilehash: 1c8bfd00452cee63456bc3bf64ccf4a0c61aa06e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-write-object-data-to-an-xml-file-c"></a><span data-ttu-id="468e1-102">Porady: wpisywanie danych o obiektach do pliku XML (C#)</span><span class="sxs-lookup"><span data-stu-id="468e1-102">How to: Write Object Data to an XML File (C#)</span></span>
<span data-ttu-id="468e1-103">W tym przykładzie zapisuje obiekt z klasy w pliku XML przy użyciu <xref:System.Xml.Serialization.XmlSerializer> klasy.</span><span class="sxs-lookup"><span data-stu-id="468e1-103">This example writes the object from a class to an XML file using the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="468e1-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="468e1-104">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="468e1-105">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="468e1-105">Compiling the Code</span></span>  
 <span data-ttu-id="468e1-106">Klasa musi mieć publicznego konstruktora bez parametrów.</span><span class="sxs-lookup"><span data-stu-id="468e1-106">The class must have a public constructor without parameters.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="468e1-107">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="468e1-107">Robust Programming</span></span>  
 <span data-ttu-id="468e1-108">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="468e1-108">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="468e1-109">Klasa poddany serializacji ma publicznego konstruktora bez parametrów.</span><span class="sxs-lookup"><span data-stu-id="468e1-109">The class being serialized does not have a public, parameterless constructor.</span></span>  
  
-   <span data-ttu-id="468e1-110">Plik istnieje i jest tylko do odczytu (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="468e1-110">The file exists and is read-only (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="468e1-111">Ścieżka jest za długa (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="468e1-111">The path is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="468e1-112">Dysk jest pełny (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="468e1-112">The disk is full (<xref:System.IO.IOException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="468e1-113">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="468e1-113">.NET Framework Security</span></span>  
 <span data-ttu-id="468e1-114">W tym przykładzie tworzy nowy plik, jeśli plik już nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="468e1-114">This example creates a new file, if the file does not already exist.</span></span> <span data-ttu-id="468e1-115">Jeśli aplikacja musi utworzyć plik, że aplikacja musi `Create` dostępu do folderu.</span><span class="sxs-lookup"><span data-stu-id="468e1-115">If an application needs to create a file, that application needs `Create` access for the folder.</span></span> <span data-ttu-id="468e1-116">Jeśli plik już istnieje, aplikacja musi tylko `Write` dostępu niższego poziomu uprawnień.</span><span class="sxs-lookup"><span data-stu-id="468e1-116">If the file already exists, the application needs only `Write` access, a lesser privilege.</span></span> <span data-ttu-id="468e1-117">Jeśli to możliwe, jest bardziej bezpieczne tworzenie pliku podczas wdrażania i udzielać tylko `Read` dostęp do jednego pliku, a nie `Create` dostępu dla folderu.</span><span class="sxs-lookup"><span data-stu-id="468e1-117">Where possible, it is more secure to create the file during deployment, and only grant `Read` access to a single file, rather than `Create` access for a folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="468e1-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="468e1-118">See Also</span></span>  
 <xref:System.IO.StreamWriter>  
 [<span data-ttu-id="468e1-119">Porady: odczytywanie danych o obiektach z pliku XML (C#)</span><span class="sxs-lookup"><span data-stu-id="468e1-119">How to: Read Object Data from an XML File (C#)</span></span>](../../../../csharp/programming-guide/concepts/serialization/how-to-read-object-data-from-an-xml-file.md)  
 [<span data-ttu-id="468e1-120">Serializacja (C#)</span><span class="sxs-lookup"><span data-stu-id="468e1-120">Serialization (C# )</span></span>](../../../../csharp/programming-guide/concepts/serialization/index.md)
