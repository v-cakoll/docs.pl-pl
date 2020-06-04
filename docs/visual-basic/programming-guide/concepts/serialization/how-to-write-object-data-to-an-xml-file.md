---
title: 'Porady: wpisywanie danych o obiektach do pliku XML'
ms.date: 07/20/2015
ms.assetid: f7966480-5ed2-43ac-9894-33427436de2a
ms.openlocfilehash: 9608a48cb8b3fac1c71affa7a0a17e9789f94b18
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413157"
---
# <a name="how-to-write-object-data-to-an-xml-file-visual-basic"></a><span data-ttu-id="7b565-102">Instrukcje: zapisywanie danych obiektu w pliku XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7b565-102">How to: Write Object Data to an XML File (Visual Basic)</span></span>
<span data-ttu-id="7b565-103">Ten przykład zapisuje obiekt z klasy do pliku XML przy użyciu <xref:System.Xml.Serialization.XmlSerializer> klasy.</span><span class="sxs-lookup"><span data-stu-id="7b565-103">This example writes the object from a class to an XML file using the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7b565-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="7b565-104">Example</span></span>  
  
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
  
## <a name="compile-the-code"></a><span data-ttu-id="7b565-105">Kompiluj kod</span><span class="sxs-lookup"><span data-stu-id="7b565-105">Compile the code</span></span>  
 <span data-ttu-id="7b565-106">Klasa musi mieć Konstruktor publiczny bez parametrów.</span><span class="sxs-lookup"><span data-stu-id="7b565-106">The class must have a public constructor without parameters.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="7b565-107">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="7b565-107">Robust Programming</span></span>  
 <span data-ttu-id="7b565-108">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="7b565-108">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="7b565-109">Serializowana Klasa nie ma publicznego konstruktora bez parametrów.</span><span class="sxs-lookup"><span data-stu-id="7b565-109">The class being serialized does not have a public, parameterless constructor.</span></span>  
  
- <span data-ttu-id="7b565-110">Plik istnieje i jest tylko do odczytu ( <xref:System.IO.IOException> ).</span><span class="sxs-lookup"><span data-stu-id="7b565-110">The file exists and is read-only (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="7b565-111">Ścieżka jest za długa ( <xref:System.IO.PathTooLongException> ).</span><span class="sxs-lookup"><span data-stu-id="7b565-111">The path is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="7b565-112">Dysk jest pełny ( <xref:System.IO.IOException> ).</span><span class="sxs-lookup"><span data-stu-id="7b565-112">The disk is full (<xref:System.IO.IOException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="7b565-113">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="7b565-113">.NET Framework Security</span></span>  
 <span data-ttu-id="7b565-114">Ten przykład tworzy nowy plik, jeśli plik jeszcze nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="7b565-114">This example creates a new file, if the file does not already exist.</span></span> <span data-ttu-id="7b565-115">Jeśli aplikacja musi utworzyć plik, aplikacja musi `Create` mieć dostęp do tego folderu.</span><span class="sxs-lookup"><span data-stu-id="7b565-115">If an application needs to create a file, that application needs `Create` access for the folder.</span></span> <span data-ttu-id="7b565-116">Jeśli plik już istnieje, aplikacja wymaga tylko `Write` dostępu, ale ma mniejsze uprawnienia.</span><span class="sxs-lookup"><span data-stu-id="7b565-116">If the file already exists, the application needs only `Write` access, a lesser privilege.</span></span> <span data-ttu-id="7b565-117">Jeśli to możliwe, bezpieczniejsze jest tworzenie pliku podczas wdrażania i udzielanie `Read` dostępu do pojedynczego pliku, a nie `Create` dostęp do folderu.</span><span class="sxs-lookup"><span data-stu-id="7b565-117">Where possible, it is more secure to create the file during deployment, and only grant `Read` access to a single file, rather than `Create` access for a folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b565-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7b565-118">See also</span></span>

- <xref:System.IO.StreamWriter>
- [<span data-ttu-id="7b565-119">Instrukcje: odczytywanie danych obiektu z pliku XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7b565-119">How to: Read Object Data from an XML File (Visual Basic)</span></span>](how-to-read-object-data-from-an-xml-file.md)
- [<span data-ttu-id="7b565-120">Serializacja (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7b565-120">Serialization (Visual Basic)</span></span>](index.md)
