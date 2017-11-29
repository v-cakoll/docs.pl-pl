---
title: 'Porady: odczytywanie danych o obiektach z pliku XML (Visual Basic)'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1e1423bf-74a4-4dde-a3bb-ae1bfc0a68ed
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 47e5c614f2083ec2c595bba9c9454ecc5f61c786
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-read-object-data-from-an-xml-file-visual-basic"></a><span data-ttu-id="fb4ec-102">Porady: odczytywanie danych o obiektach z pliku XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fb4ec-102">How to: Read Object Data from an XML File (Visual Basic)</span></span>
<span data-ttu-id="fb4ec-103">Ten przykład odczytuje danych obiektów, które zostały wcześniej zapisane do pliku XML przy użyciu <xref:System.Xml.Serialization.XmlSerializer> klasy.</span><span class="sxs-lookup"><span data-stu-id="fb4ec-103">This example reads object data that was previously written to an XML file using the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fb4ec-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="fb4ec-104">Example</span></span>  
  
```vb  
Public Class Book  
    Public Title As String  
End Class  
  
Public Sub ReadXML()  
    Dim reader As New System.Xml.Serialization.XmlSerializer(GetType(Book))  
    Dim file As New System.IO.StreamReader(  
        "c:\temp\SerializationOverview.xml")  
    Dim overview As Book  
    overview = CType(reader.Deserialize(file), Book)  
    Console.WriteLine(overview.Title)  
End Sub  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="fb4ec-105">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="fb4ec-105">Compiling the Code</span></span>  
 <span data-ttu-id="fb4ec-106">Zamień na nazwę pliku zawierającego dane serializowane nazwa pliku "c:\temp\SerializationOverview.xml".</span><span class="sxs-lookup"><span data-stu-id="fb4ec-106">Replace the file name "c:\temp\SerializationOverview.xml" with the name of the file containing the serialized data.</span></span> <span data-ttu-id="fb4ec-107">Aby uzyskać więcej informacji na temat serializacja danych, zobacz [porady: zapis danych obiektów do pliku XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md).</span><span class="sxs-lookup"><span data-stu-id="fb4ec-107">For more information about serializing data, see [How to: Write Object Data to an XML File (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md).</span></span>  
  
 <span data-ttu-id="fb4ec-108">Klasa musi mieć publicznego konstruktora bez parametrów.</span><span class="sxs-lookup"><span data-stu-id="fb4ec-108">The class must have a public constructor without parameters.</span></span>  
  
 <span data-ttu-id="fb4ec-109">Rozszeregować są tylko właściwości publiczne i pola.</span><span class="sxs-lookup"><span data-stu-id="fb4ec-109">Only public properties and fields are deserialized.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="fb4ec-110">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="fb4ec-110">Robust Programming</span></span>  
 <span data-ttu-id="fb4ec-111">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="fb4ec-111">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="fb4ec-112">Klasa poddany serializacji ma publicznego konstruktora bez parametrów.</span><span class="sxs-lookup"><span data-stu-id="fb4ec-112">The class being serialized does not have a public, parameterless constructor.</span></span>  
  
-   <span data-ttu-id="fb4ec-113">Dane w pliku nie reprezentuje dane z klasy do zdeserializowania.</span><span class="sxs-lookup"><span data-stu-id="fb4ec-113">The data in the file does not represent data from the class to be deserialized.</span></span>  
  
-   <span data-ttu-id="fb4ec-114">Plik nie istnieje (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="fb4ec-114">The file does not exist (<xref:System.IO.IOException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="fb4ec-115">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="fb4ec-115">.NET Framework Security</span></span>  
 <span data-ttu-id="fb4ec-116">Zawsze Sprawdź dane wejściowe i nigdy nie deserializować danych z niezaufanego źródła.</span><span class="sxs-lookup"><span data-stu-id="fb4ec-116">Always verify inputs, and never deserialize data from an untrusted source.</span></span> <span data-ttu-id="fb4ec-117">Uruchamia ponownie utworzyć obiekt na komputerze lokalnym przy użyciu uprawnień kodu, który go deserializacji.</span><span class="sxs-lookup"><span data-stu-id="fb4ec-117">The re-created object runs on a local computer with the permissions of the code that deserialized it.</span></span> <span data-ttu-id="fb4ec-118">Sprawdź wszystkie dane wejściowe, zanim użyjesz danych w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="fb4ec-118">Verify all inputs before using the data in your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb4ec-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fb4ec-119">See Also</span></span>  
 <xref:System.IO.StreamWriter>  
 [<span data-ttu-id="fb4ec-120">Porady: wpisywanie danych o obiektach do pliku XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fb4ec-120">How to: Write Object Data to an XML File (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md)  
 [<span data-ttu-id="fb4ec-121">Serializacja (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fb4ec-121">Serialization (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/serialization/index.md)  
 [<span data-ttu-id="fb4ec-122">Przewodnik programowania w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fb4ec-122">Visual Basic Programming Guide</span></span>](../../../../visual-basic/programming-guide/index.md)
