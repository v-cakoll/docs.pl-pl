---
title: Przykład technologii serializacji podstawowej
ms.date: 03/30/2017
ms.assetid: 9d824e16-08d1-4a36-bc7f-2388c1f75f34
ms.openlocfilehash: e5dcc9ec7cf6f996c97262b14020552286c530da
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/27/2019
ms.locfileid: "71353142"
---
# <a name="basic-serialization-technology-sample"></a><span data-ttu-id="cacad-102">Przykład technologii serializacji podstawowej</span><span class="sxs-lookup"><span data-stu-id="cacad-102">Basic Serialization Technology Sample</span></span>

[<span data-ttu-id="cacad-103">Pobieranie próbki</span><span class="sxs-lookup"><span data-stu-id="cacad-103">Download sample</span></span>](https://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Runtime%20Serialization/Basic.zip.exe)

<span data-ttu-id="cacad-104">Ten przykład pokazuje możliwości środowiska uruchomieniowego języka wspólnego do serializacji grafu obiektów w pamięci do strumienia.</span><span class="sxs-lookup"><span data-stu-id="cacad-104">This sample demonstrates the common language runtime's ability to serialize an object graph in memory to a stream.</span></span> <span data-ttu-id="cacad-105">Ten przykład może korzystać z <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> lub <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> do serializacji.</span><span class="sxs-lookup"><span data-stu-id="cacad-105">This sample can use either the <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> or the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> for serialization.</span></span> <span data-ttu-id="cacad-106">Połączonej listy wypełniany danymi, jest serializacji lub deserializacji z strumienia PLiku lub.</span><span class="sxs-lookup"><span data-stu-id="cacad-106">A linked list, filled with data, is serialized or deserialized to or from a file stream.</span></span> <span data-ttu-id="cacad-107">W obu przypadkach zostanie wyświetlona lista, aby zobaczyć wyniki.</span><span class="sxs-lookup"><span data-stu-id="cacad-107">In either case the list is displayed so that you can see the results.</span></span> <span data-ttu-id="cacad-108">Połączona lista jest typu `LinkedList`, typu zdefiniowanego przez ten przykład.</span><span class="sxs-lookup"><span data-stu-id="cacad-108">The linked list is of type `LinkedList`, a type defined by this sample.</span></span>

<span data-ttu-id="cacad-109">Komentarzy w PLikach źródłowych kodu i build.proj uzyskać więcej informacji o serializacji.</span><span class="sxs-lookup"><span data-stu-id="cacad-109">Review comments in the source code and build.proj files for more information on serialization.</span></span>

### <a name="to-build-the-sample-using-the-command-prompt"></a><span data-ttu-id="cacad-110">Aby skompilować przykład za pomocą wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="cacad-110">To build the sample using the Command Prompt</span></span>

1. <span data-ttu-id="cacad-111">Przejdź do jednego z podkatalogi specyficzne dla języka w katalogu Technologies\Serialization\Runtime Serialization\Basic, za pomocą wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="cacad-111">Navigate to one of the language-specific subdirectories under the Technologies\Serialization\Runtime Serialization\Basic directory, using the command prompt.</span></span>

2. <span data-ttu-id="cacad-112">Wpisz **MSBuild SerializationCS. sln**, **MSBuild SerializationJSL. sln** lub **MSBuild SerializationVB. sln**, w zależności od wybranego języka programowania, w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="cacad-112">Type **msbuild SerializationCS.sln**, **msbuild SerializationJSL.sln** or **msbuild SerializationVB.sln**, depending on your choice of programming language, at the command line.</span></span>

### <a name="to-build-the-sample-using-visual-studio"></a><span data-ttu-id="cacad-113">Aby skompilować przykład za pomocą programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="cacad-113">To build the sample using Visual Studio</span></span>

1. <span data-ttu-id="cacad-114">Otwórz Eksploratora plików i przejdź do jednego z podkatalogów właściwych dla języka dla przykładu.</span><span class="sxs-lookup"><span data-stu-id="cacad-114">Open File Explorer and navigate to one of the language-specific subdirectories for the sample.</span></span>

2. <span data-ttu-id="cacad-115">Kliknij dwukrotnie ikonę PLiku SerializationCS.sln, SerializationJSL.sln lub SerializationVB.sln, w zależności od wybranych przez siebie język programowania, aby otworzyć go w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="cacad-115">Double-click the icon for the SerializationCS.sln, SerializationJSL.sln or SerializationVB.sln file, depending on your choice of programming language, to open the file in Visual Studio.</span></span>

3. <span data-ttu-id="cacad-116">W menu **kompilacja** wybierz opcję **Kompiluj rozwiązanie**.</span><span class="sxs-lookup"><span data-stu-id="cacad-116">In the **Build** menu, select **Build Solution**.</span></span>

 <span data-ttu-id="cacad-117">Przykładowa aplikacja zostanie skompilowana w domyślnym podkatalogu \Bin lub \bin\Debug.</span><span class="sxs-lookup"><span data-stu-id="cacad-117">The sample application will be built in the default \bin or \bin\Debug subdirectory.</span></span>

### <a name="to-run-the-sample"></a><span data-ttu-id="cacad-118">Aby uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="cacad-118">To run the sample</span></span>

1. <span data-ttu-id="cacad-119">Przejdź do katalogu zawierającego wbudowanych PLiku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="cacad-119">Navigate to the directory containing the built executable.</span></span>

2. <span data-ttu-id="cacad-120">Wpisz **Serialization. exe**wraz z wartościami parametrów, które chcesz, w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="cacad-120">Type **Serialization.exe**, along with the parameter values you desire, at the command line.</span></span>

  > [!NOTE]
  > <span data-ttu-id="cacad-121">Ten przykład kompiluje aplikację konsolową.</span><span class="sxs-lookup"><span data-stu-id="cacad-121">This sample builds a console application.</span></span> <span data-ttu-id="cacad-122">Należy uruchomić go za pomocą wiersza polecenia, aby można było wyświetlić dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="cacad-122">You must launch it using the command prompt in order to view its output.</span></span>

## <a name="remarks"></a><span data-ttu-id="cacad-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cacad-123">Remarks</span></span>

<span data-ttu-id="cacad-124">Przykładowa aplikacja akceptuje parametry wiersza polecenia wskazujące, który test ma zostać wykonany.</span><span class="sxs-lookup"><span data-stu-id="cacad-124">The sample application accepts command line parameters indicating which test you would like to execute.</span></span> <span data-ttu-id="cacad-125">Aby serializować listę składającą się z 10 węzłów do pliku o nazwie **test. XML** przy użyciu programu formatującego protokołu SOAP, należy użyć parametrów **SX test. XML 10**.</span><span class="sxs-lookup"><span data-stu-id="cacad-125">To serialize a 10-node list to a file named **Test.xml** using the SOAP formatter, use the parameters **sx Test.xml 10**.</span></span>

<span data-ttu-id="cacad-126">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="cacad-126">For Example:</span></span>

```console
Serialize.exe -sx Test.xml 10
```

<span data-ttu-id="cacad-127">Aby zdeserializować plik **test. XML** z poprzedniego przykładu, użyj parametrów **DX test. XML**.</span><span class="sxs-lookup"><span data-stu-id="cacad-127">To deserialize the **Test.xml** file from the previous example, use the parameters **dx Test.xml**.</span></span>

<span data-ttu-id="cacad-128">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="cacad-128">For Example:</span></span>

```console
Serialize.exe -dx Test.xml
```

<span data-ttu-id="cacad-129">W dwóch przykładach powyżej "x" w przełączniku wiersza polecenia wskazuje, że chcesz serializacji SOAP XML.</span><span class="sxs-lookup"><span data-stu-id="cacad-129">In the two examples above, the "x" in the command line switch indicates that you want XML SOAP serialization.</span></span> <span data-ttu-id="cacad-130">W swoim miejscu możesz użyć "b", aby użyć serializacji binarnej.</span><span class="sxs-lookup"><span data-stu-id="cacad-130">You can use "b" in its place to use binary serialization.</span></span> <span data-ttu-id="cacad-131">Jeśli chcesz spróbować serializacji z bardzo dużej liczby węzłów, można przekierować dane wyjściowe z konsoli do PLiku.</span><span class="sxs-lookup"><span data-stu-id="cacad-131">If you wish to try serialization with a very large number of nodes, you might want to redirect the console output to a file.</span></span>

<span data-ttu-id="cacad-132">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="cacad-132">For Example:</span></span>

```console
Serialize.exe -sb Test.bin 10000 >somefile.txt
```

<span data-ttu-id="cacad-133">Poniższe punktory krótko opisują klasy i technologie używane w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="cacad-133">The following bullets briefly describe the classes and technologies used by this sample.</span></span>

- <span data-ttu-id="cacad-134">Środowisko wykonawcze serializacji</span><span class="sxs-lookup"><span data-stu-id="cacad-134">Runtime Serialization</span></span>

  - <span data-ttu-id="cacad-135"><xref:System.Runtime.Serialization.IFormatter>Służy do odwoływania się do <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> obiektu lub.</span><span class="sxs-lookup"><span data-stu-id="cacad-135"><xref:System.Runtime.Serialization.IFormatter> Used to refer to either a <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> or a <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> object.</span></span>

  - <span data-ttu-id="cacad-136"><xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>Służy do serializacji połączonej listy w strumieniu w formacie binarnym.</span><span class="sxs-lookup"><span data-stu-id="cacad-136"><xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> Used to serialize a linked list to a stream in a binary format.</span></span> <span data-ttu-id="cacad-137">Binarny program formatujący używa formatu tylko <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> rozumie typu.</span><span class="sxs-lookup"><span data-stu-id="cacad-137">The binary formatter uses a format that only the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> type understands.</span></span> <span data-ttu-id="cacad-138">Jednak dane są zwięzły.</span><span class="sxs-lookup"><span data-stu-id="cacad-138">However, the data is concise.</span></span>

  - <span data-ttu-id="cacad-139"><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>Służy do serializacji połączonej listy w strumieniu w formacie protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="cacad-139"><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> Used to serialize a linked list to a stream in the SOAP format.</span></span> <span data-ttu-id="cacad-140">Protokołu SOAP jest to standardowy format.</span><span class="sxs-lookup"><span data-stu-id="cacad-140">SOAP is a standard format.</span></span>

- <span data-ttu-id="cacad-141">We/Wy strumienia</span><span class="sxs-lookup"><span data-stu-id="cacad-141">Stream I/O</span></span>

  - <span data-ttu-id="cacad-142"><xref:System.IO.Stream>Służy do serializacji i deserializacji.</span><span class="sxs-lookup"><span data-stu-id="cacad-142"><xref:System.IO.Stream> Used to serialize and deserialize.</span></span> <span data-ttu-id="cacad-143">Typem określonego strumienia użytym w tym przykładzie jest <xref:System.IO.FileStream> typ.</span><span class="sxs-lookup"><span data-stu-id="cacad-143">The specific stream type used in this sample is the <xref:System.IO.FileStream> type.</span></span> <span data-ttu-id="cacad-144">Jednak można użyć serializacji z dowolnego typu opracowane na podstawie <xref:System.IO.Stream>.</span><span class="sxs-lookup"><span data-stu-id="cacad-144">However, serialization can be used with any type derived from <xref:System.IO.Stream>.</span></span>

  - <span data-ttu-id="cacad-145"><xref:System.IO.File>Służy do tworzenia <xref:System.IO.FileStream> obiektów do odczytu i tworzenia plików na dysku.</span><span class="sxs-lookup"><span data-stu-id="cacad-145"><xref:System.IO.File> Used to create <xref:System.IO.FileStream> objects for reading and creating files on disk.</span></span>

  - <span data-ttu-id="cacad-146"><xref:System.IO.FileStream>Używane do serializacji i deserializacji połączonych list.</span><span class="sxs-lookup"><span data-stu-id="cacad-146"><xref:System.IO.FileStream> Used to serialize and deserialize linked lists.</span></span>

## <a name="see-also"></a><span data-ttu-id="cacad-147">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cacad-147">See also</span></span>

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
- [<span data-ttu-id="cacad-148">Serializacja podstawowa</span><span class="sxs-lookup"><span data-stu-id="cacad-148">Basic Serialization</span></span>](../../../docs/standard/serialization/basic-serialization.md)
- [<span data-ttu-id="cacad-149">Serializacja binarna</span><span class="sxs-lookup"><span data-stu-id="cacad-149">Binary Serialization</span></span>](../../../docs/standard/serialization/binary-serialization.md)
- [<span data-ttu-id="cacad-150">Kontrolowanie serializacji XML przy użyciu atrybutów</span><span class="sxs-lookup"><span data-stu-id="cacad-150">Controlling XML Serialization Using Attributes</span></span>](../../../docs/standard/serialization/controlling-xml-serialization-using-attributes.md)
- [<span data-ttu-id="cacad-151">Wprowadzenie do serializacji XML</span><span class="sxs-lookup"><span data-stu-id="cacad-151">Introducing XML Serialization</span></span>](../../../docs/standard/serialization/introducing-xml-serialization.md)
- [<span data-ttu-id="cacad-152">Serializacja</span><span class="sxs-lookup"><span data-stu-id="cacad-152">Serialization</span></span>](../../../docs/standard/serialization/index.md)
- [<span data-ttu-id="cacad-153">Serializacja XML i SOAP</span><span class="sxs-lookup"><span data-stu-id="cacad-153">XML and SOAP Serialization</span></span>](../../../docs/standard/serialization/xml-and-soap-serialization.md)
