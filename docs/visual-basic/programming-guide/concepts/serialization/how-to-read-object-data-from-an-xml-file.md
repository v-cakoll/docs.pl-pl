---
title: 'Porady: odczytywanie danych o obiektach z pliku XML'
ms.date: 07/20/2015
ms.assetid: 1e1423bf-74a4-4dde-a3bb-ae1bfc0a68ed
ms.openlocfilehash: c997af4729a24a6b5bd5b22d0153860cff3282d7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346435"
---
# <a name="how-to-read-object-data-from-an-xml-file-visual-basic"></a><span data-ttu-id="af2e0-102">Instrukcje: odczytywanie danych obiektu z pliku XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="af2e0-102">How to: Read Object Data from an XML File (Visual Basic)</span></span>
<span data-ttu-id="af2e0-103">Ten przykład odczytuje dane obiektu, które wcześniej Zapisano do pliku XML przy użyciu klasy <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="af2e0-103">This example reads object data that was previously written to an XML file using the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="af2e0-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="af2e0-104">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="af2e0-105">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="af2e0-105">Compiling the Code</span></span>  
 <span data-ttu-id="af2e0-106">Zastąp nazwę pliku "c:\temp\SerializationOverview.xml" nazwą pliku zawierającego serializowane dane.</span><span class="sxs-lookup"><span data-stu-id="af2e0-106">Replace the file name "c:\temp\SerializationOverview.xml" with the name of the file containing the serialized data.</span></span> <span data-ttu-id="af2e0-107">Aby uzyskać więcej informacji na temat serializowania danych, zobacz [How to: Write dane obiektu do pliku XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md).</span><span class="sxs-lookup"><span data-stu-id="af2e0-107">For more information about serializing data, see [How to: Write Object Data to an XML File (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md).</span></span>  
  
 <span data-ttu-id="af2e0-108">Klasa musi mieć Konstruktor publiczny bez parametrów.</span><span class="sxs-lookup"><span data-stu-id="af2e0-108">The class must have a public constructor without parameters.</span></span>  
  
 <span data-ttu-id="af2e0-109">Tylko publiczne właściwości i pola są deserializowane.</span><span class="sxs-lookup"><span data-stu-id="af2e0-109">Only public properties and fields are deserialized.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="af2e0-110">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="af2e0-110">Robust Programming</span></span>  
 <span data-ttu-id="af2e0-111">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="af2e0-111">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="af2e0-112">Serializowana Klasa nie ma publicznego konstruktora bez parametrów.</span><span class="sxs-lookup"><span data-stu-id="af2e0-112">The class being serialized does not have a public, parameterless constructor.</span></span>  
  
- <span data-ttu-id="af2e0-113">Dane w pliku nie reprezentują danych z klasy, która ma zostać poddana deserializacji.</span><span class="sxs-lookup"><span data-stu-id="af2e0-113">The data in the file does not represent data from the class to be deserialized.</span></span>  
  
- <span data-ttu-id="af2e0-114">Plik nie istnieje (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="af2e0-114">The file does not exist (<xref:System.IO.IOException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="af2e0-115">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="af2e0-115">.NET Framework Security</span></span>  
 <span data-ttu-id="af2e0-116">Zawsze Weryfikuj dane wejściowe i nigdy nie wykonuj deserializacji danych z niezaufanego źródła.</span><span class="sxs-lookup"><span data-stu-id="af2e0-116">Always verify inputs, and never deserialize data from an untrusted source.</span></span> <span data-ttu-id="af2e0-117">Nowo utworzony obiekt jest uruchamiany na komputerze lokalnym z uprawnieniami kodu, który został deserializowany.</span><span class="sxs-lookup"><span data-stu-id="af2e0-117">The re-created object runs on a local computer with the permissions of the code that deserialized it.</span></span> <span data-ttu-id="af2e0-118">Sprawdź wszystkie dane wejściowe, zanim użyjesz danych w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="af2e0-118">Verify all inputs before using the data in your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af2e0-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="af2e0-119">See also</span></span>

- <xref:System.IO.StreamWriter>
- [<span data-ttu-id="af2e0-120">Instrukcje: zapisywanie danych obiektu w pliku XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="af2e0-120">How to: Write Object Data to an XML File (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md)
- [<span data-ttu-id="af2e0-121">Serializacja (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="af2e0-121">Serialization (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/serialization/index.md)
- [<span data-ttu-id="af2e0-122">Przewodnik programowania Visual Basic</span><span class="sxs-lookup"><span data-stu-id="af2e0-122">Visual Basic Programming Guide</span></span>](../../../../visual-basic/programming-guide/index.md)
