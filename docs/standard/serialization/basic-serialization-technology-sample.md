---
title: Przykład technologii serializacji podstawowej
ms.date: 03/30/2017
ms.assetid: 9d824e16-08d1-4a36-bc7f-2388c1f75f34
ms.openlocfilehash: 474eb8ded01a72182533a6d49397d7567447d64e
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2018
ms.locfileid: "45619097"
---
# <a name="basic-serialization-technology-sample"></a><span data-ttu-id="da0ba-102">Przykład technologii serializacji podstawowej</span><span class="sxs-lookup"><span data-stu-id="da0ba-102">Basic Serialization Technology Sample</span></span>
[<span data-ttu-id="da0ba-103">Pobierz przykładowe</span><span class="sxs-lookup"><span data-stu-id="da0ba-103">Download sample</span></span>](https://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Runtime%20Serialization/Basic.zip.exe)  
  
 <span data-ttu-id="da0ba-104">Niniejszy przykład pokazuje możliwość języka wspólnego serializacji grafu obiektów w pamięci w strumieniu.</span><span class="sxs-lookup"><span data-stu-id="da0ba-104">This sample demonstrates the common language runtime's ability to serialize an object graph in memory to a stream.</span></span> <span data-ttu-id="da0ba-105">W tym przykładzie można użyć dowolnego <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> lub <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> do serializacji.</span><span class="sxs-lookup"><span data-stu-id="da0ba-105">This sample can use either the <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> or the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> for serialization.</span></span> <span data-ttu-id="da0ba-106">Połączonej listy wypełniany danymi, jest serializacji lub deserializacji z strumienia PLiku lub.</span><span class="sxs-lookup"><span data-stu-id="da0ba-106">A linked list, filled with data, is serialized or deserialized to or from a file stream.</span></span> <span data-ttu-id="da0ba-107">W obu przypadkach zostanie wyświetlona lista, tak, aby zobaczyć wyniki.</span><span class="sxs-lookup"><span data-stu-id="da0ba-107">In either case the list is displayed so that you can see the results.</span></span> <span data-ttu-id="da0ba-108">Połączonej listy jest typu `LinkedList`, typ zdefiniowany przez ten przykład.</span><span class="sxs-lookup"><span data-stu-id="da0ba-108">The linked list is of type `LinkedList`, a type defined by this sample.</span></span>  
  
 <span data-ttu-id="da0ba-109">Komentarzy w PLikach źródłowych kodu i build.proj uzyskać więcej informacji o serializacji.</span><span class="sxs-lookup"><span data-stu-id="da0ba-109">Review comments in the source code and build.proj files for more information on serialization.</span></span>  
  
### <a name="to-build-the-sample-using-the-command-prompt"></a><span data-ttu-id="da0ba-110">Aby skompilować przykład za pomocą wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="da0ba-110">To build the sample using the Command Prompt</span></span>  
  
1.  <span data-ttu-id="da0ba-111">Przejdź do jednego z podkatalogi specyficzne dla języka w katalogu Technologies\Serialization\Runtime Serialization\Basic, za pomocą wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="da0ba-111">Navigate to one of the language-specific subdirectories under the Technologies\Serialization\Runtime Serialization\Basic directory, using the command prompt.</span></span>  
  
2.  <span data-ttu-id="da0ba-112">Typ **msbuild SerializationCS.sln**, **msbuild SerializationJSL.sln** lub **msbuild SerializationVB.sln**, w zależności od wybranych przez siebie język programowania, w Wiersz polecenia.</span><span class="sxs-lookup"><span data-stu-id="da0ba-112">Type **msbuild SerializationCS.sln**, **msbuild SerializationJSL.sln** or **msbuild SerializationVB.sln**, depending on your choice of programming language, at the command line.</span></span>  
  
### <a name="to-build-the-sample-using-visual-studio"></a><span data-ttu-id="da0ba-113">Aby skompilować przykład za pomocą programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="da0ba-113">To build the sample using Visual Studio</span></span>  
  
1.  <span data-ttu-id="da0ba-114">Otwórz [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] i przejdź do jednej z podkatalogi specyficzny dla języka dla próbki.</span><span class="sxs-lookup"><span data-stu-id="da0ba-114">Open [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] and navigate to one of the language-specific subdirectories for the sample.</span></span>  
  
2.  <span data-ttu-id="da0ba-115">Kliknij dwukrotnie ikonę PLiku SerializationCS.sln, SerializationJSL.sln lub SerializationVB.sln, w zależności od wybranych przez siebie język programowania, aby otworzyć go w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="da0ba-115">Double-click the icon for the SerializationCS.sln, SerializationJSL.sln or SerializationVB.sln file, depending on your choice of programming language, to open the file in Visual Studio.</span></span>  
  
3.  <span data-ttu-id="da0ba-116">W **kompilacji** menu, wybierz opcję **Kompiluj rozwiązanie**.</span><span class="sxs-lookup"><span data-stu-id="da0ba-116">In the **Build** menu, select **Build Solution**.</span></span>  
  
 <span data-ttu-id="da0ba-117">Przykładowa aplikacja zostanie utworzona w podkatalogu \bin lub \bin\Debug domyślny.</span><span class="sxs-lookup"><span data-stu-id="da0ba-117">The sample application will be built in the default \bin or \bin\Debug subdirectory.</span></span>  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="da0ba-118">Aby uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="da0ba-118">To run the sample</span></span>  
  
1.  <span data-ttu-id="da0ba-119">Przejdź do katalogu zawierającego wbudowanych PLiku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="da0ba-119">Navigate to the directory containing the built executable.</span></span>  
  
2.  <span data-ttu-id="da0ba-120">Typ **Serialization.exe**, wraz z wartościami parametru wymagasz, w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="da0ba-120">Type **Serialization.exe**, along with the parameter values you desire, at the command line.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="da0ba-121">W tym przykładzie tworzy aplikację konsoli.</span><span class="sxs-lookup"><span data-stu-id="da0ba-121">This sample builds a console application.</span></span> <span data-ttu-id="da0ba-122">Należy uruchomić go za pomocą wiersza polecenia, aby można było wyświetlić dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="da0ba-122">You must launch it using the command prompt in order to view its output.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="da0ba-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="da0ba-123">Remarks</span></span>  
 <span data-ttu-id="da0ba-124">Przykładowa aplikacja akceptuje parametry wiersza polecenia wskazujące, której można przetestować chce wykonać.</span><span class="sxs-lookup"><span data-stu-id="da0ba-124">The sample application accepts command line parameters indicating which test you would like to execute.</span></span> <span data-ttu-id="da0ba-125">Do serializacji lista 10-węzłów, w pliku o nazwie **Test.xml** przy użyciu protokołu SOAP program formatujący, użyj parametrów **sx Test.xml 10**.</span><span class="sxs-lookup"><span data-stu-id="da0ba-125">To serialize a 10-node list to a file named **Test.xml** using the SOAP formatter, use the parameters **sx Test.xml 10**.</span></span>  
  
 <span data-ttu-id="da0ba-126">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="da0ba-126">For Example:</span></span>  
  
 <span data-ttu-id="da0ba-127">**Serialize.exe - sx Test.xml 10**</span><span class="sxs-lookup"><span data-stu-id="da0ba-127">**Serialize.exe -sx Test.xml 10**</span></span>  
  
 <span data-ttu-id="da0ba-128">Do deserializacji **Test.xml** plików z poprzedniego przykładu, użyj parametrów **dx Test.xml**.</span><span class="sxs-lookup"><span data-stu-id="da0ba-128">To deserialize the **Test.xml** file from the previous example, use the parameters **dx Test.xml**.</span></span>  
  
 <span data-ttu-id="da0ba-129">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="da0ba-129">For Example:</span></span>  
  
 <span data-ttu-id="da0ba-130">**Test.xml - dx Serialize.exe**</span><span class="sxs-lookup"><span data-stu-id="da0ba-130">**Serialize.exe -dx Test.xml**</span></span>  
  
 <span data-ttu-id="da0ba-131">W dwóch przykładach w przełączniku wiersza polecenia "x" oznacza, że serializacji XML protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="da0ba-131">In the two examples above, the "x" in the command line switch indicates that you want XML SOAP serialization.</span></span> <span data-ttu-id="da0ba-132">"B" w tym miejscu służy do użycia serializacji binarnej.</span><span class="sxs-lookup"><span data-stu-id="da0ba-132">You can use "b" in its place to use binary serialization.</span></span> <span data-ttu-id="da0ba-133">Jeśli chcesz spróbować serializacji z bardzo dużej liczby węzłów, można przekierować dane wyjściowe z konsoli do PLiku.</span><span class="sxs-lookup"><span data-stu-id="da0ba-133">If you wish to try serialization with a very large number of nodes, you might want to redirect the console output to a file.</span></span>  
  
 <span data-ttu-id="da0ba-134">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="da0ba-134">For Example:</span></span>  
  
 <span data-ttu-id="da0ba-135">**Serialize.exe - sb Test.bin 10000 > somefile.txt**</span><span class="sxs-lookup"><span data-stu-id="da0ba-135">**Serialize.exe -sb Test.bin 10000 >somefile.txt**</span></span>  
  
 <span data-ttu-id="da0ba-136">Następujące punktory Zwięźle opisz klas i technologie używane w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="da0ba-136">The following bullets briefly describe the classes and technologies used by this sample.</span></span>  
  
-   <span data-ttu-id="da0ba-137">Środowisko wykonawcze serializacji</span><span class="sxs-lookup"><span data-stu-id="da0ba-137">Runtime Serialization</span></span>  
  
    -   <span data-ttu-id="da0ba-138"><xref:System.Runtime.Serialization.IFormatter>Odnosi się do albo <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> lub <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> obiektu.</span><span class="sxs-lookup"><span data-stu-id="da0ba-138"><xref:System.Runtime.Serialization.IFormatter> Used to refer to either a <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> or a <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> object.</span></span>  
  
    -   <span data-ttu-id="da0ba-139"><xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>Służy do serializacji połączonej listy w strumieniu w formacie binarnym.</span><span class="sxs-lookup"><span data-stu-id="da0ba-139"><xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> Used to serialize a linked list to a stream in a binary format.</span></span> <span data-ttu-id="da0ba-140">Binarny program formatujący używa formatu tylko <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> rozumie typu.</span><span class="sxs-lookup"><span data-stu-id="da0ba-140">The binary formatter uses a format that only the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> type understands.</span></span> <span data-ttu-id="da0ba-141">Jednak dane są zwięzły.</span><span class="sxs-lookup"><span data-stu-id="da0ba-141">However, the data is concise.</span></span>  
  
    -   <span data-ttu-id="da0ba-142"><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>Służy do serializacji połączonej listy w strumieniu w formacie protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="da0ba-142"><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> Used to serialize a linked list to a stream in the SOAP format.</span></span> <span data-ttu-id="da0ba-143">Protokołu SOAP jest to standardowy format.</span><span class="sxs-lookup"><span data-stu-id="da0ba-143">SOAP is a standard format.</span></span>  
  
-   <span data-ttu-id="da0ba-144">We/Wy strumienia</span><span class="sxs-lookup"><span data-stu-id="da0ba-144">Stream I/O</span></span>  
  
    -   <span data-ttu-id="da0ba-145"><xref:System.IO.Stream>Służy do serializacji i deserializacji.</span><span class="sxs-lookup"><span data-stu-id="da0ba-145"><xref:System.IO.Stream> Used to serialize and deserialize.</span></span> <span data-ttu-id="da0ba-146">Typ określonego strumienia używane w tym przykładzie jest <xref:System.IO.FileStream> typu.</span><span class="sxs-lookup"><span data-stu-id="da0ba-146">The specific stream type used in this sample is the <xref:System.IO.FileStream> type.</span></span> <span data-ttu-id="da0ba-147">Jednak można użyć serializacji z dowolnego typu opracowane na podstawie <xref:System.IO.Stream>.</span><span class="sxs-lookup"><span data-stu-id="da0ba-147">However, serialization can be used with any type derived from <xref:System.IO.Stream>.</span></span>  
  
    -   <span data-ttu-id="da0ba-148"><xref:System.IO.File>Służy do tworzenia <xref:System.IO.FileStream> obiektów do odczytywania i tworzenia PLików na dysku.</span><span class="sxs-lookup"><span data-stu-id="da0ba-148"><xref:System.IO.File> Used to create <xref:System.IO.FileStream> objects for reading and creating files on disk.</span></span>  
  
    -   <span data-ttu-id="da0ba-149"><xref:System.IO.FileStream>Służy do serializacji i deserializacji połączonej listy.</span><span class="sxs-lookup"><span data-stu-id="da0ba-149"><xref:System.IO.FileStream> Used to serialize and deserialize linked lists.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da0ba-150">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="da0ba-150">See also</span></span>

- <xref:System.IO>  
- <xref:System.IO.File>  
- <xref:System.IO.FileStream>  
- <xref:System.IO.Stream>  
- <xref:System.Random>  
- <xref:System.Runtime.Serialization>  
- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>  
- <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>  
- <xref:System.Runtime.Serialization.IFormatter>  
- <xref:System.SerializableAttribute>  
- <xref:System.Xml.Serialization>  
- [<span data-ttu-id="da0ba-151">Serializacja podstawowa</span><span class="sxs-lookup"><span data-stu-id="da0ba-151">Basic Serialization</span></span>](../../../docs/standard/serialization/basic-serialization.md)  
- [<span data-ttu-id="da0ba-152">Serializacja binarna</span><span class="sxs-lookup"><span data-stu-id="da0ba-152">Binary Serialization</span></span>](../../../docs/standard/serialization/binary-serialization.md)  
- [<span data-ttu-id="da0ba-153">Kontrolowanie serializacji XML przy użyciu atrybutów</span><span class="sxs-lookup"><span data-stu-id="da0ba-153">Controlling XML Serialization Using Attributes</span></span>](../../../docs/standard/serialization/controlling-xml-serialization-using-attributes.md)  
- [<span data-ttu-id="da0ba-154">Wprowadzenie do serializacji XML</span><span class="sxs-lookup"><span data-stu-id="da0ba-154">Introducing XML Serialization</span></span>](../../../docs/standard/serialization/introducing-xml-serialization.md)  
- [<span data-ttu-id="da0ba-155">Serializacja</span><span class="sxs-lookup"><span data-stu-id="da0ba-155">Serialization</span></span>](../../../docs/standard/serialization/index.md)  
- [<span data-ttu-id="da0ba-156">Serializacja XML i SOAP</span><span class="sxs-lookup"><span data-stu-id="da0ba-156">XML and SOAP Serialization</span></span>](../../../docs/standard/serialization/xml-and-soap-serialization.md)
