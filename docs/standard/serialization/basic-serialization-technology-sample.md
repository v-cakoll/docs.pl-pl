---
title: Przykład technologii serializacji podstawowej
description: Ten przykład ilustruje możliwość wykonywania serializacji grafu obiektów w pamięci do strumienia. Ten przykład może używać SoapFormatter lub BinaryFormatter.
ms.date: 03/30/2017
ms.assetid: 9d824e16-08d1-4a36-bc7f-2388c1f75f34
ms.openlocfilehash: fcbf790c3b3d48a0aeb27fd1ef6f75dcd7609ae0
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378443"
---
# <a name="basic-serialization-technology-sample"></a><span data-ttu-id="e2fd3-104">Przykład technologii serializacji podstawowej</span><span class="sxs-lookup"><span data-stu-id="e2fd3-104">Basic Serialization Technology Sample</span></span>

[<span data-ttu-id="e2fd3-105">Pobieranie próbki</span><span class="sxs-lookup"><span data-stu-id="e2fd3-105">Download sample</span></span>](https://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Runtime%20Serialization/Basic.zip.exe)

<span data-ttu-id="e2fd3-106">Ten przykład pokazuje możliwości środowiska uruchomieniowego języka wspólnego do serializacji grafu obiektów w pamięci do strumienia.</span><span class="sxs-lookup"><span data-stu-id="e2fd3-106">This sample demonstrates the common language runtime's ability to serialize an object graph in memory to a stream.</span></span> <span data-ttu-id="e2fd3-107">Ten przykład może korzystać z <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> lub do <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> serializacji.</span><span class="sxs-lookup"><span data-stu-id="e2fd3-107">This sample can use either the <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> or the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> for serialization.</span></span> <span data-ttu-id="e2fd3-108">Połączonej listy wypełniany danymi, jest serializacji lub deserializacji z strumienia PLiku lub.</span><span class="sxs-lookup"><span data-stu-id="e2fd3-108">A linked list, filled with data, is serialized or deserialized to or from a file stream.</span></span> <span data-ttu-id="e2fd3-109">W obu przypadkach zostanie wyświetlona lista, aby zobaczyć wyniki.</span><span class="sxs-lookup"><span data-stu-id="e2fd3-109">In either case the list is displayed so that you can see the results.</span></span> <span data-ttu-id="e2fd3-110">Połączona lista jest typu `LinkedList` , typu zdefiniowanego przez ten przykład.</span><span class="sxs-lookup"><span data-stu-id="e2fd3-110">The linked list is of type `LinkedList`, a type defined by this sample.</span></span>

<span data-ttu-id="e2fd3-111">Komentarzy w PLikach źródłowych kodu i build.proj uzyskać więcej informacji o serializacji.</span><span class="sxs-lookup"><span data-stu-id="e2fd3-111">Review comments in the source code and build.proj files for more information on serialization.</span></span>

### <a name="to-build-the-sample-using-the-command-prompt"></a><span data-ttu-id="e2fd3-112">Aby skompilować przykład za pomocą wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="e2fd3-112">To build the sample using the Command Prompt</span></span>

1. <span data-ttu-id="e2fd3-113">Przejdź do jednego z podkatalogi specyficzne dla języka w katalogu Technologies\Serialization\Runtime Serialization\Basic, za pomocą wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="e2fd3-113">Navigate to one of the language-specific subdirectories under the Technologies\Serialization\Runtime Serialization\Basic directory, using the command prompt.</span></span>

2. <span data-ttu-id="e2fd3-114">Wpisz **MSBuild SerializationCS. sln**, **MSBuild SerializationJSL. sln** lub **MSBuild SerializationVB. sln**, w zależności od wybranego języka programowania, w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="e2fd3-114">Type **msbuild SerializationCS.sln**, **msbuild SerializationJSL.sln** or **msbuild SerializationVB.sln**, depending on your choice of programming language, at the command line.</span></span>

### <a name="to-build-the-sample-using-visual-studio"></a><span data-ttu-id="e2fd3-115">Aby skompilować przykład za pomocą programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e2fd3-115">To build the sample using Visual Studio</span></span>

1. <span data-ttu-id="e2fd3-116">Otwórz Eksploratora plików i przejdź do jednego z podkatalogów właściwych dla języka dla przykładu.</span><span class="sxs-lookup"><span data-stu-id="e2fd3-116">Open File Explorer and navigate to one of the language-specific subdirectories for the sample.</span></span>

2. <span data-ttu-id="e2fd3-117">Kliknij dwukrotnie ikonę PLiku SerializationCS.sln, SerializationJSL.sln lub SerializationVB.sln, w zależności od wybranych przez siebie język programowania, aby otworzyć go w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e2fd3-117">Double-click the icon for the SerializationCS.sln, SerializationJSL.sln or SerializationVB.sln file, depending on your choice of programming language, to open the file in Visual Studio.</span></span>

3. <span data-ttu-id="e2fd3-118">W menu **kompilacja** wybierz opcję **Kompiluj rozwiązanie**.</span><span class="sxs-lookup"><span data-stu-id="e2fd3-118">In the **Build** menu, select **Build Solution**.</span></span>

 <span data-ttu-id="e2fd3-119">Przykładowa aplikacja zostanie skompilowana w domyślnym podkatalogu \Bin lub \bin\Debug.</span><span class="sxs-lookup"><span data-stu-id="e2fd3-119">The sample application will be built in the default \bin or \bin\Debug subdirectory.</span></span>

### <a name="to-run-the-sample"></a><span data-ttu-id="e2fd3-120">Aby uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="e2fd3-120">To run the sample</span></span>

1. <span data-ttu-id="e2fd3-121">Przejdź do katalogu zawierającego wbudowanych PLiku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="e2fd3-121">Navigate to the directory containing the built executable.</span></span>

2. <span data-ttu-id="e2fd3-122">Wpisz **Serialization. exe**wraz z wartościami parametrów, które chcesz, w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="e2fd3-122">Type **Serialization.exe**, along with the parameter values you desire, at the command line.</span></span>

  > [!NOTE]
  > <span data-ttu-id="e2fd3-123">Ten przykład kompiluje aplikację konsolową.</span><span class="sxs-lookup"><span data-stu-id="e2fd3-123">This sample builds a console application.</span></span> <span data-ttu-id="e2fd3-124">Należy uruchomić go za pomocą wiersza polecenia, aby można było wyświetlić dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="e2fd3-124">You must launch it using the command prompt in order to view its output.</span></span>

## <a name="remarks"></a><span data-ttu-id="e2fd3-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e2fd3-125">Remarks</span></span>

<span data-ttu-id="e2fd3-126">Przykładowa aplikacja akceptuje parametry wiersza polecenia wskazujące, który test ma zostać wykonany.</span><span class="sxs-lookup"><span data-stu-id="e2fd3-126">The sample application accepts command line parameters indicating which test you would like to execute.</span></span> <span data-ttu-id="e2fd3-127">Aby serializować listę składającą się z 10 węzłów do pliku o nazwie **test. XML** przy użyciu programu formatującego protokołu SOAP, należy użyć parametrów **SX test. XML 10**.</span><span class="sxs-lookup"><span data-stu-id="e2fd3-127">To serialize a 10-node list to a file named **Test.xml** using the SOAP formatter, use the parameters **sx Test.xml 10**.</span></span>

<span data-ttu-id="e2fd3-128">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="e2fd3-128">For Example:</span></span>

```console
Serialize.exe -sx Test.xml 10
```

<span data-ttu-id="e2fd3-129">Aby zdeserializować plik **test. XML** z poprzedniego przykładu, użyj parametrów **DX test. XML**.</span><span class="sxs-lookup"><span data-stu-id="e2fd3-129">To deserialize the **Test.xml** file from the previous example, use the parameters **dx Test.xml**.</span></span>

<span data-ttu-id="e2fd3-130">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="e2fd3-130">For Example:</span></span>

```console
Serialize.exe -dx Test.xml
```

<span data-ttu-id="e2fd3-131">W dwóch przykładach powyżej "x" w przełączniku wiersza polecenia wskazuje, że chcesz serializacji SOAP XML.</span><span class="sxs-lookup"><span data-stu-id="e2fd3-131">In the two examples above, the "x" in the command line switch indicates that you want XML SOAP serialization.</span></span> <span data-ttu-id="e2fd3-132">W swoim miejscu możesz użyć "b", aby użyć serializacji binarnej.</span><span class="sxs-lookup"><span data-stu-id="e2fd3-132">You can use "b" in its place to use binary serialization.</span></span> <span data-ttu-id="e2fd3-133">Jeśli chcesz spróbować serializacji z bardzo dużej liczby węzłów, można przekierować dane wyjściowe z konsoli do PLiku.</span><span class="sxs-lookup"><span data-stu-id="e2fd3-133">If you wish to try serialization with a very large number of nodes, you might want to redirect the console output to a file.</span></span>

<span data-ttu-id="e2fd3-134">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="e2fd3-134">For Example:</span></span>

```console
Serialize.exe -sb Test.bin 10000 >somefile.txt
```

<span data-ttu-id="e2fd3-135">Poniższe punktory krótko opisują klasy i technologie używane w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="e2fd3-135">The following bullets briefly describe the classes and technologies used by this sample.</span></span>

- <span data-ttu-id="e2fd3-136">Środowisko wykonawcze serializacji</span><span class="sxs-lookup"><span data-stu-id="e2fd3-136">Runtime Serialization</span></span>

  - <span data-ttu-id="e2fd3-137"><xref:System.Runtime.Serialization.IFormatter>Służy do odwoływania się do <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> obiektu lub <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> .</span><span class="sxs-lookup"><span data-stu-id="e2fd3-137"><xref:System.Runtime.Serialization.IFormatter> Used to refer to either a <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> or a <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> object.</span></span>

  - <span data-ttu-id="e2fd3-138"><xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>Służy do serializacji połączonej listy w strumieniu w formacie binarnym.</span><span class="sxs-lookup"><span data-stu-id="e2fd3-138"><xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> Used to serialize a linked list to a stream in a binary format.</span></span> <span data-ttu-id="e2fd3-139">Binarny program formatujący używa formatu tylko <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> rozumie typu.</span><span class="sxs-lookup"><span data-stu-id="e2fd3-139">The binary formatter uses a format that only the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> type understands.</span></span> <span data-ttu-id="e2fd3-140">Jednak dane są zwięzły.</span><span class="sxs-lookup"><span data-stu-id="e2fd3-140">However, the data is concise.</span></span>

  - <span data-ttu-id="e2fd3-141"><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>Służy do serializacji połączonej listy w strumieniu w formacie protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="e2fd3-141"><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> Used to serialize a linked list to a stream in the SOAP format.</span></span> <span data-ttu-id="e2fd3-142">Protokołu SOAP jest to standardowy format.</span><span class="sxs-lookup"><span data-stu-id="e2fd3-142">SOAP is a standard format.</span></span>

- <span data-ttu-id="e2fd3-143">We/Wy strumienia</span><span class="sxs-lookup"><span data-stu-id="e2fd3-143">Stream I/O</span></span>

  - <span data-ttu-id="e2fd3-144"><xref:System.IO.Stream>Służy do serializacji i deserializacji.</span><span class="sxs-lookup"><span data-stu-id="e2fd3-144"><xref:System.IO.Stream> Used to serialize and deserialize.</span></span> <span data-ttu-id="e2fd3-145">Typem określonego strumienia użytym w tym przykładzie jest <xref:System.IO.FileStream> Typ.</span><span class="sxs-lookup"><span data-stu-id="e2fd3-145">The specific stream type used in this sample is the <xref:System.IO.FileStream> type.</span></span> <span data-ttu-id="e2fd3-146">Jednak można użyć serializacji z dowolnego typu opracowane na podstawie <xref:System.IO.Stream>.</span><span class="sxs-lookup"><span data-stu-id="e2fd3-146">However, serialization can be used with any type derived from <xref:System.IO.Stream>.</span></span>

  - <span data-ttu-id="e2fd3-147"><xref:System.IO.File>Służy do tworzenia <xref:System.IO.FileStream> obiektów do odczytu i tworzenia plików na dysku.</span><span class="sxs-lookup"><span data-stu-id="e2fd3-147"><xref:System.IO.File> Used to create <xref:System.IO.FileStream> objects for reading and creating files on disk.</span></span>

  - <span data-ttu-id="e2fd3-148"><xref:System.IO.FileStream>Używane do serializacji i deserializacji połączonych list.</span><span class="sxs-lookup"><span data-stu-id="e2fd3-148"><xref:System.IO.FileStream> Used to serialize and deserialize linked lists.</span></span>

## <a name="see-also"></a><span data-ttu-id="e2fd3-149">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e2fd3-149">See also</span></span>

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
- [<span data-ttu-id="e2fd3-150">Serializacja podstawowa</span><span class="sxs-lookup"><span data-stu-id="e2fd3-150">Basic Serialization</span></span>](../../../docs/standard/serialization/basic-serialization.md)
- [<span data-ttu-id="e2fd3-151">Serializacja binarna</span><span class="sxs-lookup"><span data-stu-id="e2fd3-151">Binary Serialization</span></span>](../../../docs/standard/serialization/binary-serialization.md)
- [<span data-ttu-id="e2fd3-152">Kontrolowanie serializacji XML przy użyciu atrybutów</span><span class="sxs-lookup"><span data-stu-id="e2fd3-152">Controlling XML Serialization Using Attributes</span></span>](../../../docs/standard/serialization/controlling-xml-serialization-using-attributes.md)
- [<span data-ttu-id="e2fd3-153">Wprowadzenie do serializacji XML</span><span class="sxs-lookup"><span data-stu-id="e2fd3-153">Introducing XML Serialization</span></span>](../../../docs/standard/serialization/introducing-xml-serialization.md)
- [<span data-ttu-id="e2fd3-154">Serializacja</span><span class="sxs-lookup"><span data-stu-id="e2fd3-154">Serialization</span></span>](../../../docs/standard/serialization/index.md)
- [<span data-ttu-id="e2fd3-155">Serializacja XML i SOAP</span><span class="sxs-lookup"><span data-stu-id="e2fd3-155">XML and SOAP Serialization</span></span>](../../../docs/standard/serialization/xml-and-soap-serialization.md)
