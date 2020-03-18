---
title: Jak zapisywać dane obiektu do pliku XML (C#)
ms.date: 07/20/2015
ms.assetid: 7681eb98-703d-4005-a369-26a7bca0f894
ms.openlocfilehash: f7ffb47a22d3cd94cd7cb6f702b64180a8790eb4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79167517"
---
# <a name="how-to-write-object-data-to-an-xml-file-c"></a><span data-ttu-id="31dc5-102">Jak zapisywać dane obiektu do pliku XML (C#)</span><span class="sxs-lookup"><span data-stu-id="31dc5-102">How to write object data to an XML file (C#)</span></span>
<span data-ttu-id="31dc5-103">W tym przykładzie zapisuje obiekt z klasy do <xref:System.Xml.Serialization.XmlSerializer> pliku XML przy użyciu klasy.</span><span class="sxs-lookup"><span data-stu-id="31dc5-103">This example writes the object from a class to an XML file using the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="31dc5-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="31dc5-104">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="31dc5-105">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="31dc5-105">Compiling the Code</span></span>  
 <span data-ttu-id="31dc5-106">Klasa serializacji musi mieć konstruktora publicznego bez parametrów.</span><span class="sxs-lookup"><span data-stu-id="31dc5-106">The class being serialized must have a public constructor without parameters.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="31dc5-107">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="31dc5-107">Robust Programming</span></span>  
 <span data-ttu-id="31dc5-108">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="31dc5-108">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="31dc5-109">Klasa serializacji nie ma konstruktora publicznego, bezparametrów.</span><span class="sxs-lookup"><span data-stu-id="31dc5-109">The class being serialized does not have a public, parameterless constructor.</span></span>  
  
- <span data-ttu-id="31dc5-110">Plik istnieje i jest tylko<xref:System.IO.IOException>do odczytu ( ).</span><span class="sxs-lookup"><span data-stu-id="31dc5-110">The file exists and is read-only (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="31dc5-111">Ścieżka jest zbyt<xref:System.IO.PathTooLongException>długa ( ).</span><span class="sxs-lookup"><span data-stu-id="31dc5-111">The path is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="31dc5-112">Dysk jest zapełniony (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="31dc5-112">The disk is full (<xref:System.IO.IOException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="31dc5-113">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="31dc5-113">.NET Framework Security</span></span>  
 <span data-ttu-id="31dc5-114">W tym przykładzie tworzy nowy plik, jeśli plik jeszcze nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="31dc5-114">This example creates a new file, if the file does not already exist.</span></span> <span data-ttu-id="31dc5-115">Jeśli aplikacja musi utworzyć plik, ta `Create` aplikacja wymaga dostępu do folderu.</span><span class="sxs-lookup"><span data-stu-id="31dc5-115">If an application needs to create a file, that application needs `Create` access for the folder.</span></span> <span data-ttu-id="31dc5-116">Jeśli plik już istnieje, aplikacja `Write` wymaga tylko dostępu, mniejsze uprawnienia.</span><span class="sxs-lookup"><span data-stu-id="31dc5-116">If the file already exists, the application needs only `Write` access, a lesser privilege.</span></span> <span data-ttu-id="31dc5-117">Jeśli to możliwe, jest bardziej bezpieczne, aby utworzyć `Read` plik podczas wdrażania i `Create` przyznać dostęp tylko do jednego pliku, a nie dostęp do folderu.</span><span class="sxs-lookup"><span data-stu-id="31dc5-117">Where possible, it is more secure to create the file during deployment, and only grant `Read` access to a single file, rather than `Create` access for a folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31dc5-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="31dc5-118">See also</span></span>

- <xref:System.IO.StreamWriter>
- [<span data-ttu-id="31dc5-119">Jak odczytywać dane obiektu z pliku XML (C#)</span><span class="sxs-lookup"><span data-stu-id="31dc5-119">How to read object data from an XML file (C#)</span></span>](./how-to-read-object-data-from-an-xml-file.md)
- [<span data-ttu-id="31dc5-120">Serializacja (C#)</span><span class="sxs-lookup"><span data-stu-id="31dc5-120">Serialization (C#)</span></span>](./index.md)
