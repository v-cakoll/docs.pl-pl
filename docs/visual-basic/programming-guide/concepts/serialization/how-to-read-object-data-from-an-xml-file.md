---
title: 'Instrukcje: Odczytywanie danych o obiektach z pliku XML (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 1e1423bf-74a4-4dde-a3bb-ae1bfc0a68ed
ms.openlocfilehash: f6233fc7ce74cbd39237bab07cfd2ed22b9c2240
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58834897"
---
# <a name="how-to-read-object-data-from-an-xml-file-visual-basic"></a><span data-ttu-id="5cc23-102">Instrukcje: Odczytywanie danych o obiektach z pliku XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5cc23-102">How to: Read Object Data from an XML File (Visual Basic)</span></span>
<span data-ttu-id="5cc23-103">W tym przykładzie odczytuje dane obiektów, które zostały wcześniej zapisane do pliku XML przy użyciu <xref:System.Xml.Serialization.XmlSerializer> klasy.</span><span class="sxs-lookup"><span data-stu-id="5cc23-103">This example reads object data that was previously written to an XML file using the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5cc23-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="5cc23-104">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="5cc23-105">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="5cc23-105">Compiling the Code</span></span>  
 <span data-ttu-id="5cc23-106">Nazwa pliku "c:\temp\SerializationOverview.xml" należy zastąpić nazwę pliku zawierającego dane serializowane.</span><span class="sxs-lookup"><span data-stu-id="5cc23-106">Replace the file name "c:\temp\SerializationOverview.xml" with the name of the file containing the serialized data.</span></span> <span data-ttu-id="5cc23-107">Aby uzyskać więcej informacji na temat serializowania danych zobacz [jak: Zapisywania obiektów danych do pliku XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md).</span><span class="sxs-lookup"><span data-stu-id="5cc23-107">For more information about serializing data, see [How to: Write Object Data to an XML File (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md).</span></span>  
  
 <span data-ttu-id="5cc23-108">Klasa musi mieć publicznego konstruktora bez parametrów.</span><span class="sxs-lookup"><span data-stu-id="5cc23-108">The class must have a public constructor without parameters.</span></span>  
  
 <span data-ttu-id="5cc23-109">Tylko właściwości publiczne i pola są deserializacji.</span><span class="sxs-lookup"><span data-stu-id="5cc23-109">Only public properties and fields are deserialized.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="5cc23-110">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="5cc23-110">Robust Programming</span></span>  
 <span data-ttu-id="5cc23-111">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="5cc23-111">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="5cc23-112">Klasa jest serializowana, nie ma publiczny konstruktor bez parametrów.</span><span class="sxs-lookup"><span data-stu-id="5cc23-112">The class being serialized does not have a public, parameterless constructor.</span></span>  
  
-   <span data-ttu-id="5cc23-113">Dane w pliku nie reprezentuje dane z klasy, która ma zostać przeprowadzona.</span><span class="sxs-lookup"><span data-stu-id="5cc23-113">The data in the file does not represent data from the class to be deserialized.</span></span>  
  
-   <span data-ttu-id="5cc23-114">Plik nie istnieje (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="5cc23-114">The file does not exist (<xref:System.IO.IOException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="5cc23-115">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="5cc23-115">.NET Framework Security</span></span>  
 <span data-ttu-id="5cc23-116">Zawsze sprawdzić dane wejściowe i nigdy nie deserializowanie danych z niezaufanego źródła.</span><span class="sxs-lookup"><span data-stu-id="5cc23-116">Always verify inputs, and never deserialize data from an untrusted source.</span></span> <span data-ttu-id="5cc23-117">Ponownie utworzyć obiekt działa na komputerze lokalnym z uprawnieniami kod, który deserializacji go.</span><span class="sxs-lookup"><span data-stu-id="5cc23-117">The re-created object runs on a local computer with the permissions of the code that deserialized it.</span></span> <span data-ttu-id="5cc23-118">Sprawdź wszystkie dane wejściowe, zanim użyjesz danych w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5cc23-118">Verify all inputs before using the data in your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5cc23-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5cc23-119">See also</span></span>

- <xref:System.IO.StreamWriter>
- [<span data-ttu-id="5cc23-120">Instrukcje: Zapisywania obiektów danych do pliku XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5cc23-120">How to: Write Object Data to an XML File (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md)
- [<span data-ttu-id="5cc23-121">Serializacja (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5cc23-121">Serialization (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/serialization/index.md)
- [<span data-ttu-id="5cc23-122">Przewodnik programowania w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5cc23-122">Visual Basic Programming Guide</span></span>](../../../../visual-basic/programming-guide/index.md)
