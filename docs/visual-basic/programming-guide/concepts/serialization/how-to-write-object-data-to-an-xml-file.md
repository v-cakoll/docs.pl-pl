---
title: 'Porady: wpisywanie danych o obiektach do pliku XML (Visual Basic)'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f7966480-5ed2-43ac-9894-33427436de2a
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: df461f9b560dac45add0d7c82ff4938b0a7b1e62
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-write-object-data-to-an-xml-file-visual-basic"></a><span data-ttu-id="1bdc8-102">Porady: wpisywanie danych o obiektach do pliku XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1bdc8-102">How to: Write Object Data to an XML File (Visual Basic)</span></span>
<span data-ttu-id="1bdc8-103">W tym przykładzie zapisuje obiekt z klasy w pliku XML przy użyciu <xref:System.Xml.Serialization.XmlSerializer> klasy.</span><span class="sxs-lookup"><span data-stu-id="1bdc8-103">This example writes the object from a class to an XML file using the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1bdc8-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="1bdc8-104">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="1bdc8-105">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="1bdc8-105">Compiling the Code</span></span>  
 <span data-ttu-id="1bdc8-106">Klasa musi mieć publicznego konstruktora bez parametrów.</span><span class="sxs-lookup"><span data-stu-id="1bdc8-106">The class must have a public constructor without parameters.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="1bdc8-107">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="1bdc8-107">Robust Programming</span></span>  
 <span data-ttu-id="1bdc8-108">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="1bdc8-108">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="1bdc8-109">Klasa poddany serializacji ma publicznego konstruktora bez parametrów.</span><span class="sxs-lookup"><span data-stu-id="1bdc8-109">The class being serialized does not have a public, parameterless constructor.</span></span>  
  
-   <span data-ttu-id="1bdc8-110">Plik istnieje i jest tylko do odczytu (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="1bdc8-110">The file exists and is read-only (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="1bdc8-111">Ścieżka jest za długa (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="1bdc8-111">The path is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="1bdc8-112">Dysk jest pełny (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="1bdc8-112">The disk is full (<xref:System.IO.IOException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="1bdc8-113">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="1bdc8-113">.NET Framework Security</span></span>  
 <span data-ttu-id="1bdc8-114">W tym przykładzie tworzy nowy plik, jeśli plik już nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="1bdc8-114">This example creates a new file, if the file does not already exist.</span></span> <span data-ttu-id="1bdc8-115">Jeśli aplikacja musi utworzyć plik, że aplikacja musi `Create` dostępu do folderu.</span><span class="sxs-lookup"><span data-stu-id="1bdc8-115">If an application needs to create a file, that application needs `Create` access for the folder.</span></span> <span data-ttu-id="1bdc8-116">Jeśli plik już istnieje, aplikacja musi tylko `Write` dostępu niższego poziomu uprawnień.</span><span class="sxs-lookup"><span data-stu-id="1bdc8-116">If the file already exists, the application needs only `Write` access, a lesser privilege.</span></span> <span data-ttu-id="1bdc8-117">Jeśli to możliwe, jest bardziej bezpieczne tworzenie pliku podczas wdrażania i udzielać tylko `Read` dostęp do jednego pliku, a nie `Create` dostępu dla folderu.</span><span class="sxs-lookup"><span data-stu-id="1bdc8-117">Where possible, it is more secure to create the file during deployment, and only grant `Read` access to a single file, rather than `Create` access for a folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bdc8-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1bdc8-118">See Also</span></span>  
 <xref:System.IO.StreamWriter>  
 [<span data-ttu-id="1bdc8-119">Porady: odczytywanie danych o obiektach z pliku XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1bdc8-119">How to: Read Object Data from an XML File (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/serialization/how-to-read-object-data-from-an-xml-file.md)  
 [<span data-ttu-id="1bdc8-120">Serializacja (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1bdc8-120">Serialization (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/serialization/index.md)
