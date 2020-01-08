---
title: 'Porady: wpisywanie danych o obiektach do pliku XML'
ms.date: 07/20/2015
ms.assetid: f7966480-5ed2-43ac-9894-33427436de2a
ms.openlocfilehash: 989920709428f0e9cb4ddb8aeacfc71a2df220d2
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345975"
---
# <a name="how-to-write-object-data-to-an-xml-file-visual-basic"></a><span data-ttu-id="53814-102">Instrukcje: zapisywanie danych obiektu w pliku XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="53814-102">How to: Write Object Data to an XML File (Visual Basic)</span></span>
<span data-ttu-id="53814-103">Ten przykład zapisuje obiekt z klasy do pliku XML przy użyciu klasy <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="53814-103">This example writes the object from a class to an XML file using the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="53814-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="53814-104">Example</span></span>  
  
```vb  
Public Module XMLWrite  
  
    Sub Main()  
        WriteXML()  
    End Sub  
  
    Public Class Book  
        Public Title As String  
    End Class  
  
    Public Sub WriteXML()  
        Dim overview As New Book  
        overview.Title = "Serialization Overview"  
        Dim writer As New System.Xml.Serialization.XmlSerializer(GetType(Book))  
        Dim file As New System.IO.StreamWriter(  
            "c:\temp\SerializationOverview.xml")  
        writer.Serialize(file, overview)  
        file.Close()  
    End Sub  
End Module  
```  
  
## <a name="compile-the-code"></a><span data-ttu-id="53814-105">Skompilować kod</span><span class="sxs-lookup"><span data-stu-id="53814-105">Compile the code</span></span>  
 <span data-ttu-id="53814-106">Klasa musi mieć Konstruktor publiczny bez parametrów.</span><span class="sxs-lookup"><span data-stu-id="53814-106">The class must have a public constructor without parameters.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="53814-107">Skuteczne programowanie</span><span class="sxs-lookup"><span data-stu-id="53814-107">Robust Programming</span></span>  
 <span data-ttu-id="53814-108">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="53814-108">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="53814-109">Serializowana Klasa nie ma publicznego konstruktora bez parametrów.</span><span class="sxs-lookup"><span data-stu-id="53814-109">The class being serialized does not have a public, parameterless constructor.</span></span>  
  
- <span data-ttu-id="53814-110">Plik istnieje i jest tylko do odczytu (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="53814-110">The file exists and is read-only (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="53814-111">Ścieżka jest za długa (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="53814-111">The path is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="53814-112">Dysk jest pełny (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="53814-112">The disk is full (<xref:System.IO.IOException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="53814-113">Zabezpieczenia programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="53814-113">.NET Framework Security</span></span>  
 <span data-ttu-id="53814-114">Ten przykład tworzy nowy plik, jeśli plik jeszcze nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="53814-114">This example creates a new file, if the file does not already exist.</span></span> <span data-ttu-id="53814-115">Jeśli aplikacja musi utworzyć plik, ta aplikacja wymaga `Create` dostępu do folderu.</span><span class="sxs-lookup"><span data-stu-id="53814-115">If an application needs to create a file, that application needs `Create` access for the folder.</span></span> <span data-ttu-id="53814-116">Jeśli plik już istnieje, aplikacja wymaga tylko `Write` dostępu, ale ma mniejsze uprawnienia.</span><span class="sxs-lookup"><span data-stu-id="53814-116">If the file already exists, the application needs only `Write` access, a lesser privilege.</span></span> <span data-ttu-id="53814-117">Jeśli to możliwe, bezpieczniejsze jest tworzenie plików podczas wdrażania i udzielanie `Read` dostęp do pojedynczego pliku, a nie `Create` dostępu do folderu.</span><span class="sxs-lookup"><span data-stu-id="53814-117">Where possible, it is more secure to create the file during deployment, and only grant `Read` access to a single file, rather than `Create` access for a folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53814-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="53814-118">See also</span></span>

- <xref:System.IO.StreamWriter>
- [<span data-ttu-id="53814-119">Instrukcje: odczytywanie danych obiektu z pliku XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="53814-119">How to: Read Object Data from an XML File (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/serialization/how-to-read-object-data-from-an-xml-file.md)
- [<span data-ttu-id="53814-120">Serializacja (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="53814-120">Serialization (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/serialization/index.md)
