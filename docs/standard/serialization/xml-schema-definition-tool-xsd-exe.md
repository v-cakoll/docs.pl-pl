---
title: "Narzędzie definicji schematu XML (Xsd.exe)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a6e6e65c-347f-4494-9457-653bf29baac2
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 31bb350d454d2fcb0f38d092240c98c1b87966be
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="xml-schema-definition-tool-xsdexe"></a><span data-ttu-id="329b1-102">Narzędzie definicji schematu XML (Xsd.exe)</span><span class="sxs-lookup"><span data-stu-id="329b1-102">XML Schema Definition Tool (Xsd.exe)</span></span>
<span data-ttu-id="329b1-103">Narzędzie definicji schematu XML (Xsd.exe) generuje schemat XML lub wspólnej klasy środowiska wykonawczego języka z PLików XDR, XML i XSD lub klasy w zestawie czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="329b1-103">The XML Schema Definition (Xsd.exe) tool generates XML schema or common language runtime classes from XDR, XML, and XSD files, or from classes in a runtime assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="329b1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="329b1-104">Syntax</span></span>  
  
```  
xsd file.xdr [/outputdir:directory][/parameters:file.xml]  
xsd file.xml [/outputdir:directory] [/parameters:file.xml]  
xsd file.xsd {/classes | /dataset} [/element:element]   
             [/enableLinqDataSet] [/language:language]   
                          [/namespace:namespace] [/outputdir:directory] [URI:uri]   
                          [/parameters:file.xml]  
xsd {file.dll | file.exe} [/outputdir:directory] [/type:typename [...]][/parameters:file.xml]  
```  
  
## <a name="argument"></a><span data-ttu-id="329b1-105">Argument</span><span class="sxs-lookup"><span data-stu-id="329b1-105">Argument</span></span>  
  
|<span data-ttu-id="329b1-106">Argument</span><span class="sxs-lookup"><span data-stu-id="329b1-106">Argument</span></span>|<span data-ttu-id="329b1-107">Opis</span><span class="sxs-lookup"><span data-stu-id="329b1-107">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="329b1-108">*File.Extension*</span><span class="sxs-lookup"><span data-stu-id="329b1-108">*file.extension*</span></span>|<span data-ttu-id="329b1-109">Określa PLik wejściowy można przekonwertować.</span><span class="sxs-lookup"><span data-stu-id="329b1-109">Specifies the input file to convert.</span></span> <span data-ttu-id="329b1-110">Należy określić extensionas, jeden z następujących: .xdr, XML, XSD, .dll lub .exe.</span><span class="sxs-lookup"><span data-stu-id="329b1-110">You must specify the extensionas one of the following: .xdr, .xml, .xsd, .dll, or .exe.</span></span><br /><br /> <span data-ttu-id="329b1-111">Jeśli określono PLik schematu XDR (rozszerzenie .xdr), Xsd.exe konwertuje schematu XDR schematu XSD.</span><span class="sxs-lookup"><span data-stu-id="329b1-111">If you specify an XDR schema file (.xdr extension), Xsd.exe converts the XDR schema to an XSD schema.</span></span> <span data-ttu-id="329b1-112">PLik wyjściowy ma taką samą nazwę schematu XDR, ale z rozszerzeniem xsd.</span><span class="sxs-lookup"><span data-stu-id="329b1-112">The output file has the same name as the XDR schema, but with the .xsd extension.</span></span><br /><br /> <span data-ttu-id="329b1-113">Jeśli określono PLik XML (rozszerzenie .xml), Xsd.exe wymaga schematu z danych w PLiku i tworzy schematu XSD.</span><span class="sxs-lookup"><span data-stu-id="329b1-113">If you specify an XML file (.xml extension), Xsd.exe infers a schema from the data in the file and produces an XSD schema.</span></span> <span data-ttu-id="329b1-114">PLik wyjściowy ma taką samą nazwę jak PLik XML, ale z rozszerzeniem xsd.</span><span class="sxs-lookup"><span data-stu-id="329b1-114">The output file has the same name as the XML file, but with the .xsd extension.</span></span><br /><br /> <span data-ttu-id="329b1-115">Jeśli określono PLik schematu XML (XSD rozszerzenia), Xsd.exe generuje kod źródłowy środowiska wykonawczego obiektów, które odpowiadają schematu XML.</span><span class="sxs-lookup"><span data-stu-id="329b1-115">If you specify an XML schema file (.xsd extension), Xsd.exe generates source code for runtime objects that correspond to the XML schema.</span></span><br /><br /> <span data-ttu-id="329b1-116">Jeśli określono PLik zestawu runtime (z rozszerzeniem .exe lub .dll), Xsd.exe generuje schematów dla co najmniej jeden typ w tym zestawie.</span><span class="sxs-lookup"><span data-stu-id="329b1-116">If you specify a runtime assembly file (.exe or .dll extension), Xsd.exe generates schemas for one or more types in that assembly.</span></span> <span data-ttu-id="329b1-117">Można użyć `/type` opcję, aby określić typy, dla których mają być generowanie schematów.</span><span class="sxs-lookup"><span data-stu-id="329b1-117">You can use the `/type` option to specify the types for which to generate schemas.</span></span> <span data-ttu-id="329b1-118">Schematy dane wyjściowe są nazywane schema0.xsd, schema1.xsd i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="329b1-118">The output schemas are named schema0.xsd, schema1.xsd, and so on.</span></span> <span data-ttu-id="329b1-119">XSD.exe tworzy wiele schematów tylko wtedy, gdy w danym typami Określ, za pomocą przestrzeni nazw `XMLRoot` atrybutu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="329b1-119">Xsd.exe produces multiple schemas only if the given types specify a namespace using the `XMLRoot` custom attribute.</span></span>|  
  
## <a name="general-options"></a><span data-ttu-id="329b1-120">Opcje ogólne</span><span class="sxs-lookup"><span data-stu-id="329b1-120">General Options</span></span>  
  
|<span data-ttu-id="329b1-121">Opcja</span><span class="sxs-lookup"><span data-stu-id="329b1-121">Option</span></span>|<span data-ttu-id="329b1-122">Opis</span><span class="sxs-lookup"><span data-stu-id="329b1-122">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="329b1-123">**/h**[**elp**]</span><span class="sxs-lookup"><span data-stu-id="329b1-123">**/h**[**elp**]</span></span>|<span data-ttu-id="329b1-124">Wyświetla składnię polecenia i opcje narzędzia.</span><span class="sxs-lookup"><span data-stu-id="329b1-124">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="329b1-125">**/o**[**utputdir**]**:***katalogu*</span><span class="sxs-lookup"><span data-stu-id="329b1-125">**/o**[**utputdir**]**:***directory*</span></span>|<span data-ttu-id="329b1-126">Określa katalog danych dla PLików danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="329b1-126">Specifies the directory for output files.</span></span> <span data-ttu-id="329b1-127">Ten argument może wystąpić tylko raz.</span><span class="sxs-lookup"><span data-stu-id="329b1-127">This argument can appear only once.</span></span> <span data-ttu-id="329b1-128">Ustawieniem domyślnym jest bieżący katalog.</span><span class="sxs-lookup"><span data-stu-id="329b1-128">The default is the current directory.</span></span>|  
|<span data-ttu-id="329b1-129">**/?**</span><span class="sxs-lookup"><span data-stu-id="329b1-129">**/?**</span></span>|<span data-ttu-id="329b1-130">Wyświetla składnię polecenia i opcje narzędzia.</span><span class="sxs-lookup"><span data-stu-id="329b1-130">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="329b1-131">**/P [arameters]:** *file.xml*</span><span class="sxs-lookup"><span data-stu-id="329b1-131">**/P[arameters]:** *file.xml*</span></span>|<span data-ttu-id="329b1-132">Opcje dla różnych trybach operacji odczytu z PLiku .xml określony.</span><span class="sxs-lookup"><span data-stu-id="329b1-132">Read options for various operation modes from the specified .xml file.</span></span> <span data-ttu-id="329b1-133">Formularz Skrócony jest "/ p:".</span><span class="sxs-lookup"><span data-stu-id="329b1-133">The short form is '/p:'.</span></span> <span data-ttu-id="329b1-134">Aby uzyskać więcej informacji zobacz następujące sekcji uwag.</span><span class="sxs-lookup"><span data-stu-id="329b1-134">For more information, see the following Remarks section.</span></span>|  
  
## <a name="xsd-file-options"></a><span data-ttu-id="329b1-135">Opcje PLiku XSD</span><span class="sxs-lookup"><span data-stu-id="329b1-135">XSD File Options</span></span>  
 <span data-ttu-id="329b1-136">Należy określić tylko jedną z poniższych opcji dotyczących XSD PLików.</span><span class="sxs-lookup"><span data-stu-id="329b1-136">You must specify only one of the following options for .xsd files.</span></span>  
  
|<span data-ttu-id="329b1-137">Opcja</span><span class="sxs-lookup"><span data-stu-id="329b1-137">Option</span></span>|<span data-ttu-id="329b1-138">Opis</span><span class="sxs-lookup"><span data-stu-id="329b1-138">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="329b1-139">**/c**[**zy**]</span><span class="sxs-lookup"><span data-stu-id="329b1-139">**/c**[**lasses**]</span></span>|<span data-ttu-id="329b1-140">Generuje klasy, które odpowiadają określony schemat.</span><span class="sxs-lookup"><span data-stu-id="329b1-140">Generates classes that correspond to the specified schema.</span></span> <span data-ttu-id="329b1-141">Do odczytywania danych XML do obiektu, należy użyć `System.Xml.Serialization.XmlSerializer.Deserializer` metody.</span><span class="sxs-lookup"><span data-stu-id="329b1-141">To read XML data into the object, use the `System.Xml.Serialization.XmlSerializer.Deserializer` method.</span></span>|  
|<span data-ttu-id="329b1-142">**/d**[**ataset**]</span><span class="sxs-lookup"><span data-stu-id="329b1-142">**/d**[**ataset**]</span></span>|<span data-ttu-id="329b1-143">Generuje klasę pochodną <xref:System.Data.DataSet> , który odpowiada określony schemat.</span><span class="sxs-lookup"><span data-stu-id="329b1-143">Generates a class derived from <xref:System.Data.DataSet> that corresponds to the specified schema.</span></span> <span data-ttu-id="329b1-144">Do odczytywania danych XML w klasie pochodnej, użyj `System.Data.DataSet.ReadXml` metody.</span><span class="sxs-lookup"><span data-stu-id="329b1-144">To read XML data into the derived class, use the `System.Data.DataSet.ReadXml` method.</span></span>|  
  
 <span data-ttu-id="329b1-145">Można również określić jedną z poniższych opcji dotyczących XSD PLików.</span><span class="sxs-lookup"><span data-stu-id="329b1-145">You can also specify any of the following options for .xsd files.</span></span>  
  
|<span data-ttu-id="329b1-146">Opcja</span><span class="sxs-lookup"><span data-stu-id="329b1-146">Option</span></span>|<span data-ttu-id="329b1-147">Opis</span><span class="sxs-lookup"><span data-stu-id="329b1-147">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="329b1-148">**/e**[**lementu**]**:***— element*</span><span class="sxs-lookup"><span data-stu-id="329b1-148">**/e**[**lement**]**:***element*</span></span>|<span data-ttu-id="329b1-149">Określa schemat do generowania kodu dla elementu.</span><span class="sxs-lookup"><span data-stu-id="329b1-149">Specifies the element in the schema to generate code for.</span></span> <span data-ttu-id="329b1-150">Domyślnie wszystkie elementy są wpisane.</span><span class="sxs-lookup"><span data-stu-id="329b1-150">By default all elements are typed.</span></span> <span data-ttu-id="329b1-151">Tego argumentu można określić więcej niż raz.</span><span class="sxs-lookup"><span data-stu-id="329b1-151">You can specify this argument more than once.</span></span>|  
|<span data-ttu-id="329b1-152">**/enableDataBinding**</span><span class="sxs-lookup"><span data-stu-id="329b1-152">**/enableDataBinding**</span></span>|<span data-ttu-id="329b1-153">Implementuje <xref:System.ComponentModel.INotifyPropertyChanged> interfejsu na wszystkich typach wygenerowanego do włączenia możliwości wiązania danych.</span><span class="sxs-lookup"><span data-stu-id="329b1-153">Implements the <xref:System.ComponentModel.INotifyPropertyChanged> interface on all generated types to enable data binding.</span></span> <span data-ttu-id="329b1-154">Krótka forma jest `/edb`.</span><span class="sxs-lookup"><span data-stu-id="329b1-154">The short form is `/edb`.</span></span>|  
|<span data-ttu-id="329b1-155">**/enableLinqDataSet**</span><span class="sxs-lookup"><span data-stu-id="329b1-155">**/enableLinqDataSet**</span></span>|<span data-ttu-id="329b1-156">(Skrócona forma: `/eld`.) Określa, że wygenerowanego zestawu danych mogą być wyszukiwane względem przy użyciu LINQ do zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="329b1-156">(Short form: `/eld`.) Specifies that the generated DataSet can be queried against using LINQ to DataSet.</span></span> <span data-ttu-id="329b1-157">Ta opcja jest stosowana, gdy określona jest również opcja /dataset.</span><span class="sxs-lookup"><span data-stu-id="329b1-157">This option is used when the /dataset option is also specified.</span></span> <span data-ttu-id="329b1-158">Aby uzyskać więcej informacji, zobacz [LINQ do DataSet omówienie](../../../docs/framework/data/adonet/linq-to-dataset-overview.md) i [zapytań wpisanych zestawów danych](../../../docs/framework/data/adonet/querying-typed-datasets.md).</span><span class="sxs-lookup"><span data-stu-id="329b1-158">For more information, see [LINQ to DataSet Overview](../../../docs/framework/data/adonet/linq-to-dataset-overview.md) and [Querying Typed DataSets](../../../docs/framework/data/adonet/querying-typed-datasets.md).</span></span> <span data-ttu-id="329b1-159">Aby uzyskać ogólne informacje dotyczące korzystania z LINQ, zobacz [LINQ (zapytania język Language-Integrated)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d).</span><span class="sxs-lookup"><span data-stu-id="329b1-159">For general information about using LINQ, see [LINQ (Language-Integrated Query)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d).</span></span>|  
|<span data-ttu-id="329b1-160">**/f**[**pola**]</span><span class="sxs-lookup"><span data-stu-id="329b1-160">**/f**[**ields**]</span></span>|<span data-ttu-id="329b1-161">Generuje pola, a nie właściwości.</span><span class="sxs-lookup"><span data-stu-id="329b1-161">Generates fields instead of properties.</span></span> <span data-ttu-id="329b1-162">Domyślnie są generowane, właściwości.</span><span class="sxs-lookup"><span data-stu-id="329b1-162">By default, properties are generated.</span></span>|  
|<span data-ttu-id="329b1-163">**/l**[**ęzyk**]**:***języka*</span><span class="sxs-lookup"><span data-stu-id="329b1-163">**/l**[**anguage**]**:***language*</span></span>|<span data-ttu-id="329b1-164">Określa język programowania.</span><span class="sxs-lookup"><span data-stu-id="329b1-164">Specifies the programming language to use.</span></span> <span data-ttu-id="329b1-165">Wybierz z `CS` (C#, który jest domyślnie), `VB` (Visual Basic), `JS` (JScript) lub `VJS` (Visual J#).</span><span class="sxs-lookup"><span data-stu-id="329b1-165">Choose from `CS` (C#, which is the default), `VB` (Visual Basic), `JS` (JScript), or `VJS` (Visual J#).</span></span> <span data-ttu-id="329b1-166">Można również określić pełną nazwę Implementacja klasy<xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="329b1-166">You can also specify a fully qualified name for a class implementing <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType></span></span>|  
|<span data-ttu-id="329b1-167">**/n**[**amespace**]**:***przestrzeni nazw*</span><span class="sxs-lookup"><span data-stu-id="329b1-167">**/n**[**amespace**]**:***namespace*</span></span>|<span data-ttu-id="329b1-168">Określa przestrzeń nazw czasu wykonywania wygenerowany typów.</span><span class="sxs-lookup"><span data-stu-id="329b1-168">Specifies the runtime namespace for the generated types.</span></span> <span data-ttu-id="329b1-169">Domyślny obszar nazw jest `Schemas`.</span><span class="sxs-lookup"><span data-stu-id="329b1-169">The default namespace is `Schemas`.</span></span>|  
|<span data-ttu-id="329b1-170">**/ nologo**</span><span class="sxs-lookup"><span data-stu-id="329b1-170">**/nologo**</span></span>|<span data-ttu-id="329b1-171">Pomija transparentu.</span><span class="sxs-lookup"><span data-stu-id="329b1-171">Suppresses the banner.</span></span>|  
|<span data-ttu-id="329b1-172">**/ ORDER**</span><span class="sxs-lookup"><span data-stu-id="329b1-172">**/order**</span></span>|<span data-ttu-id="329b1-173">Generuje jawne kolejności identyfikatorów dla wszystkich członków cząstek.</span><span class="sxs-lookup"><span data-stu-id="329b1-173">Generates explicit order identifiers on all particle members.</span></span>|  
|<span data-ttu-id="329b1-174">**/o [ut]:** *directoryName*</span><span class="sxs-lookup"><span data-stu-id="329b1-174">**/o[ut]:** *directoryName*</span></span>|<span data-ttu-id="329b1-175">Określa katalog wyjściowy, który można umieścić pliki w.</span><span class="sxs-lookup"><span data-stu-id="329b1-175">Specifies the output directory to place the files in.</span></span> <span data-ttu-id="329b1-176">Ustawieniem domyślnym jest bieżący katalog.</span><span class="sxs-lookup"><span data-stu-id="329b1-176">The default is the current directory.</span></span>|  
|<span data-ttu-id="329b1-177">**/u**[**ri**]**:***identyfikatora uri*</span><span class="sxs-lookup"><span data-stu-id="329b1-177">**/u**[**ri**]**:***uri*</span></span>|<span data-ttu-id="329b1-178">Określa identyfikator URI dla elementów w schemacie do generowania kodu.</span><span class="sxs-lookup"><span data-stu-id="329b1-178">Specifies the URI for the elements in the schema to generate code for.</span></span> <span data-ttu-id="329b1-179">Ten identyfikator URI, jeśli jest dostępna ma zastosowanie do wszystkich elementów określony za pomocą `/element` opcji.</span><span class="sxs-lookup"><span data-stu-id="329b1-179">This URI, if present, applies to all elements specified with the `/element` option.</span></span>|  
  
## <a name="dll-and-exe-file-options"></a><span data-ttu-id="329b1-180">Biblioteka DLL i opcje PLiku EXE</span><span class="sxs-lookup"><span data-stu-id="329b1-180">DLL and EXE File Options</span></span>  
  
|<span data-ttu-id="329b1-181">Opcja</span><span class="sxs-lookup"><span data-stu-id="329b1-181">Option</span></span>|<span data-ttu-id="329b1-182">Opis</span><span class="sxs-lookup"><span data-stu-id="329b1-182">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="329b1-183">**/t**[**ypu**]**:***typename*</span><span class="sxs-lookup"><span data-stu-id="329b1-183">**/t**[**ype**]**:***typename*</span></span>|<span data-ttu-id="329b1-184">Określa nazwę typu można utworzyć schemat.</span><span class="sxs-lookup"><span data-stu-id="329b1-184">Specifies the name of the type to create a schema for.</span></span> <span data-ttu-id="329b1-185">Można określić wiele argumentów typu.</span><span class="sxs-lookup"><span data-stu-id="329b1-185">You can specify multiple type arguments.</span></span> <span data-ttu-id="329b1-186">Jeśli *typename* nie określa przestrzeni nazw, dopasowań Xsd.exe wszystkie typy w zestawie z określonym typem.</span><span class="sxs-lookup"><span data-stu-id="329b1-186">If *typename* does not specify a namespace, Xsd.exe matches all types in the assembly with the specified type.</span></span> <span data-ttu-id="329b1-187">Jeśli *typename* Określa przestrzeń nazw, tylko że typ jest zgodne.</span><span class="sxs-lookup"><span data-stu-id="329b1-187">If *typename* specifies a namespace, only that type is matched.</span></span> <span data-ttu-id="329b1-188">Jeśli *typename* kończy się znakiem gwiazdki (\*), narzędzie dopasowuje wszystkie typy, które rozpoczyna się od ciągu poprzednich \*.</span><span class="sxs-lookup"><span data-stu-id="329b1-188">If *typename* ends with an asterisk character (\*), the tool matches all types that start with the string preceding the \*.</span></span> <span data-ttu-id="329b1-189">W przypadku pominięcia `/type` opcji Xsd.exe generuje schematów dla wszystkich typów w zestawie.</span><span class="sxs-lookup"><span data-stu-id="329b1-189">If you omit the `/type` option, Xsd.exe generates schemas for all types in the assembly.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="329b1-190">Uwagi</span><span class="sxs-lookup"><span data-stu-id="329b1-190">Remarks</span></span>  
 <span data-ttu-id="329b1-191">W poniższej tabeli przedstawiono operacje, że Xsd.exe wykonuje.</span><span class="sxs-lookup"><span data-stu-id="329b1-191">The following table shows the operations that Xsd.exe performs.</span></span>  
  
 <span data-ttu-id="329b1-192">XDR do XSD</span><span class="sxs-lookup"><span data-stu-id="329b1-192">XDR to XSD</span></span>  
 <span data-ttu-id="329b1-193">Generuje schematu XML na podstawie PLiku schematu obniżonej danych XML.</span><span class="sxs-lookup"><span data-stu-id="329b1-193">Generates an XML schema from an XML-Data-Reduced schema file.</span></span> <span data-ttu-id="329b1-194">XDR jest wczesne format schematu oparty na formacie XML.</span><span class="sxs-lookup"><span data-stu-id="329b1-194">XDR is an early XML-based schema format.</span></span>  
  
 <span data-ttu-id="329b1-195">XML do XSD</span><span class="sxs-lookup"><span data-stu-id="329b1-195">XML to XSD</span></span>  
 <span data-ttu-id="329b1-196">Generuje schematu XML z PLiku XML.</span><span class="sxs-lookup"><span data-stu-id="329b1-196">Generates an XML schema from an XML file.</span></span>  
  
 <span data-ttu-id="329b1-197">XSD do zestawu danych</span><span class="sxs-lookup"><span data-stu-id="329b1-197">XSD to DataSet</span></span>  
 <span data-ttu-id="329b1-198">Generuje aparatu PLików wykonywalnych języka wspólnego <xref:System.Data.DataSet> klasy z PLiku schematu XSD.</span><span class="sxs-lookup"><span data-stu-id="329b1-198">Generates common language runtime <xref:System.Data.DataSet> classes from an XSD schema file.</span></span> <span data-ttu-id="329b1-199">Wygenerowany klasy zapewnić model obiektu sformatowanego regularnych danych XML.</span><span class="sxs-lookup"><span data-stu-id="329b1-199">The generated classes provide a rich object model for regular XML data.</span></span>  
  
 <span data-ttu-id="329b1-200">XSD do klasy</span><span class="sxs-lookup"><span data-stu-id="329b1-200">XSD to Classes</span></span>  
 <span data-ttu-id="329b1-201">Generuje klasy środowiska wykonawczego na podstawie PLiku schematu XSD.</span><span class="sxs-lookup"><span data-stu-id="329b1-201">Generates runtime classes from an XSD schema file.</span></span> <span data-ttu-id="329b1-202">Wygenerowany klasy mogą być używane w połączeniu z <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> do odczytu i zapisu kod XML, który jest zgodna z schemat.</span><span class="sxs-lookup"><span data-stu-id="329b1-202">The generated classes can be used in conjunction with <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> to read and write XML code that follows the schema.</span></span>  
  
 <span data-ttu-id="329b1-203">Klasy do XSD</span><span class="sxs-lookup"><span data-stu-id="329b1-203">Classes to XSD</span></span>  
 <span data-ttu-id="329b1-204">Generuje schematu XML na podstawie typ lub typy w PLiku zestawu czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="329b1-204">Generates an XML schema from a type or types in a runtime assembly file.</span></span> <span data-ttu-id="329b1-205">Wygenerowany schemat definiuje format XML używany przez `System.Xml.Serialization.XmlSerializer`.</span><span class="sxs-lookup"><span data-stu-id="329b1-205">The generated schema defines the XML format used by `System.Xml.Serialization.XmlSerializer`.</span></span>  
  
 <span data-ttu-id="329b1-206">XSD.exe służy tylko do modyfikowania schematów XML, które podlegają języka definicji schematu XML (XSD) proponowanych przez konsorcjum World Wide Web (W3C).</span><span class="sxs-lookup"><span data-stu-id="329b1-206">Xsd.exe only allows you to manipulate XML schemas that follow the XML Schema Definition (XSD) language proposed by the World Wide Web Consortium (W3C).</span></span> <span data-ttu-id="329b1-207">Aby uzyskać więcej informacji na propozycję definicji schematu XML lub standardu XML zobacz http://w3.org.</span><span class="sxs-lookup"><span data-stu-id="329b1-207">For more information on the XML Schema Definition proposal or the XML standard, see http://w3.org.</span></span>  
  
## <a name="setting-options-with-an-xml-file"></a><span data-ttu-id="329b1-208">Ustawianie opcji z PLiku XML</span><span class="sxs-lookup"><span data-stu-id="329b1-208">Setting Options with an XML File</span></span>  
 <span data-ttu-id="329b1-209">Za pomocą `/parameters` przełącznika, można określić pojedynczy plik XML, która ustawia różne opcje.</span><span class="sxs-lookup"><span data-stu-id="329b1-209">By using the `/parameters` switch, you can specify a single XML file that sets various options.</span></span> <span data-ttu-id="329b1-210">Opcje, które można ustawić zależą od sposobu korzystania z narzędzia XSD.exe.</span><span class="sxs-lookup"><span data-stu-id="329b1-210">The options you can set depend on how you are using the XSD.exe tool.</span></span> <span data-ttu-id="329b1-211">Można także wybrać opcję generowania schematy, generowanie kodu PLików lub generowania kodu PLiki, które zawierają `DataSet` funkcji.</span><span class="sxs-lookup"><span data-stu-id="329b1-211">Choices include generating schemas, generating code files, or generating code files that include `DataSet` features.</span></span> <span data-ttu-id="329b1-212">Na przykład można ustawić `<assembly\>` element na nazwę pliku wykonywalnego (.exe) lub typu biblioteki (.dll) pliku podczas generowania schematu, ale nie podczas generowania pliku kodu.</span><span class="sxs-lookup"><span data-stu-id="329b1-212">For example, you can set the `<assembly\>` element to the name of an executable (.exe) or type library (.dll) file when generating a schema, but not when generating a code file.</span></span> <span data-ttu-id="329b1-213">Następujące kodu XML przedstawiono sposoby używania `<generateSchemas\>` element z określonego PLiku wykonywalnego:</span><span class="sxs-lookup"><span data-stu-id="329b1-213">The following XML shows how to use the `<generateSchemas\>` element with a specified executable:</span></span>  
  
```xml  
<!-- This is in a file named GenerateSchemas.xml. -->  
<xsd xmlns='http://microsoft.com/dotnet/tools/xsd/'>  
<generateSchemas>  
   <assembly>ConsoleApplication1.exe</assembly>  
</generateSchemas>  
</xsd>  
```  
  
 <span data-ttu-id="329b1-214">Jeśli poprzedni kod XML znajduje się w pliku o nazwie GenerateSchemas.xml, użyj `/parameters` przełącznika, wpisując następujące polecenie w wierszu polecenia i naciskając klawisz ENTER:</span><span class="sxs-lookup"><span data-stu-id="329b1-214">If the preceding XML is contained in a file named GenerateSchemas.xml, then use the `/parameters` switch by typing the following at a command prompt and pressing ENTER:</span></span>  
  
 `xsd /p:GenerateSchemas.xml`  
  
 <span data-ttu-id="329b1-215">Z drugiej strony jest generowany schematu dla pojedynczego typu znaleziony w zestawie, można użyć następującego kodu XML:</span><span class="sxs-lookup"><span data-stu-id="329b1-215">On the other hand, if you are generating a schema for a single type found in the assembly, you can use the following XML:</span></span>  
  
```xml  
<!-- This is in a file named GenerateSchemaFromType.xml. -->  
<xsd xmlns='http://microsoft.com/dotnet/tools/xsd/'>  
<generateSchemas>  
   <type>IDItems</type>  
</generateSchemas>  
</xsd>  
```  
  
 <span data-ttu-id="329b1-216">Jednak aby użyć poprzedni kod, należy również podać nazwę zestawu w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="329b1-216">But to use preceding code, you must also supply the name of the assembly at the command prompt.</span></span> <span data-ttu-id="329b1-217">Wpisz w wierszu polecenia (przy założeniu, że PLik XML jest o nazwie GenerateSchemaFromType.xml):</span><span class="sxs-lookup"><span data-stu-id="329b1-217">Type the following at a command prompt (presuming the XML file is named GenerateSchemaFromType.xml):</span></span>  
  
 `xsd /p:GenerateSchemaFromType.xml ConsoleApplication1.exe`  
  
 <span data-ttu-id="329b1-218">Należy określić tylko jedną z poniższych opcji dotyczących `\<generateSchemas>` elementu.</span><span class="sxs-lookup"><span data-stu-id="329b1-218">You must specify only one of the following options for the `\<generateSchemas>` element.</span></span>  
  
|<span data-ttu-id="329b1-219">Element</span><span class="sxs-lookup"><span data-stu-id="329b1-219">Element</span></span>|<span data-ttu-id="329b1-220">Opis</span><span class="sxs-lookup"><span data-stu-id="329b1-220">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="329b1-221">\<zestaw ></span><span class="sxs-lookup"><span data-stu-id="329b1-221">\<assembly></span></span>|<span data-ttu-id="329b1-222">Określa generowanie schematu z zestawu.</span><span class="sxs-lookup"><span data-stu-id="329b1-222">Specifies an assembly to generate the schema from.</span></span>|  
|<span data-ttu-id="329b1-223">\<Typ ></span><span class="sxs-lookup"><span data-stu-id="329b1-223">\<type></span></span>|<span data-ttu-id="329b1-224">Określa typ odnaleźć w zestawie do generowania schemat.</span><span class="sxs-lookup"><span data-stu-id="329b1-224">Specifies a type found in an assembly to generate a schema for.</span></span>|  
|<span data-ttu-id="329b1-225">\<XML ></span><span class="sxs-lookup"><span data-stu-id="329b1-225">\<xml></span></span>|<span data-ttu-id="329b1-226">Określa PLik XML do generowania schemat.</span><span class="sxs-lookup"><span data-stu-id="329b1-226">Specifies an XML file to generate a schema for.</span></span>|  
|<span data-ttu-id="329b1-227">\<XDR ></span><span class="sxs-lookup"><span data-stu-id="329b1-227">\<xdr></span></span>|<span data-ttu-id="329b1-228">Określa PLik XDR do generowania schemat.</span><span class="sxs-lookup"><span data-stu-id="329b1-228">Specifies an XDR file to generate a schema for.</span></span>|  
  
 <span data-ttu-id="329b1-229">Aby wygenerować PLik kodu, należy użyć `<generateClasses\>` elementu.</span><span class="sxs-lookup"><span data-stu-id="329b1-229">To generate a code file, use the `<generateClasses\>` element.</span></span> <span data-ttu-id="329b1-230">Poniższy przykład umożliwia wygenerowanie pliku kodu.</span><span class="sxs-lookup"><span data-stu-id="329b1-230">The following example generates a code file.</span></span> <span data-ttu-id="329b1-231">Należy zauważyć, że dwa atrybuty są także wyświetlane, która pozwala na ustawienie języka programowania i przestrzeni nazw w wygenerowanym PLiku.</span><span class="sxs-lookup"><span data-stu-id="329b1-231">Note that two attributes are also shown that allow you to set the programming language and namespace of the generated file.</span></span>  
  
```xml  
<xsd xmlns='http://microsoft.com/dotnet/tools/xsd/'>  
<generateClasses language='VB' namespace='Microsoft.Serialization.Examples'/>  
</xsd>  
<!-- You must supply an .xsd file when typing in the command line.-->  
<!-- For example: xsd /p:genClasses mySchema.xsd -->  
```  
  
 <span data-ttu-id="329b1-232">Można ustawić dla opcji `\<generateClasses>` obejmują elementu.</span><span class="sxs-lookup"><span data-stu-id="329b1-232">Options you can set for the `\<generateClasses>` element include the following.</span></span>  
  
|<span data-ttu-id="329b1-233">Element</span><span class="sxs-lookup"><span data-stu-id="329b1-233">Element</span></span>|<span data-ttu-id="329b1-234">Opis</span><span class="sxs-lookup"><span data-stu-id="329b1-234">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="329b1-235">\<Element ></span><span class="sxs-lookup"><span data-stu-id="329b1-235">\<element></span></span>|<span data-ttu-id="329b1-236">Określa PLik XSD do generowania kodu dla elementu.</span><span class="sxs-lookup"><span data-stu-id="329b1-236">Specifies an element in the .xsd file to generate code for.</span></span>|  
|<span data-ttu-id="329b1-237">\<schemaImporterExtensions ></span><span class="sxs-lookup"><span data-stu-id="329b1-237">\<schemaImporterExtensions></span></span>|<span data-ttu-id="329b1-238">Określa typ pochodzący od <xref:System.Xml.Serialization.Advanced.SchemaImporterExtension> klasy.</span><span class="sxs-lookup"><span data-stu-id="329b1-238">Specifies a type derived from the <xref:System.Xml.Serialization.Advanced.SchemaImporterExtension> class.</span></span>|  
|<span data-ttu-id="329b1-239">\<Schemat ></span><span class="sxs-lookup"><span data-stu-id="329b1-239">\<schema></span></span>|<span data-ttu-id="329b1-240">Określa PLik schematu XML do generowania kodu.</span><span class="sxs-lookup"><span data-stu-id="329b1-240">Specifies a XML Schema file to generate code for.</span></span>  <span data-ttu-id="329b1-241">Wiele plików schematów XML można określić przy użyciu wielu \<schematu > elementów.</span><span class="sxs-lookup"><span data-stu-id="329b1-241">Multiple XML Schema files can be specified using multiple \<schema> elements.</span></span>|  
  
 <span data-ttu-id="329b1-242">Poniższa tabela zawiera atrybuty, które umożliwia także z `<generateClasses\>` elementu.</span><span class="sxs-lookup"><span data-stu-id="329b1-242">The following table shows the attributes that can also be used with the `<generateClasses\>` element.</span></span>  
  
|<span data-ttu-id="329b1-243">Atrybut</span><span class="sxs-lookup"><span data-stu-id="329b1-243">Attribute</span></span>|<span data-ttu-id="329b1-244">Opis</span><span class="sxs-lookup"><span data-stu-id="329b1-244">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="329b1-245">język</span><span class="sxs-lookup"><span data-stu-id="329b1-245">language</span></span>|<span data-ttu-id="329b1-246">Określa język programowania.</span><span class="sxs-lookup"><span data-stu-id="329b1-246">Specifies the programming language to use.</span></span> <span data-ttu-id="329b1-247">Wybierz z `CS` (C#, wartość domyślna), `VB` (Visual Basic), `JS` (JScript) lub `VJS` (Visual J#).</span><span class="sxs-lookup"><span data-stu-id="329b1-247">Choose from `CS` (C#, the default), `VB` (Visual Basic), `JS` (JScript), or `VJS` (Visual J#).</span></span> <span data-ttu-id="329b1-248">Można również określić pełną nazwę klasy, która implementuje <xref:System.CodeDom.Compiler.CodeDomProvider>.</span><span class="sxs-lookup"><span data-stu-id="329b1-248">You can also specify a fully qualified name for a class that implements <xref:System.CodeDom.Compiler.CodeDomProvider>.</span></span>|  
|<span data-ttu-id="329b1-249">— przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="329b1-249">namespace</span></span>|<span data-ttu-id="329b1-250">Określa przestrzeń nazw dla wygenerowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="329b1-250">Specifies the namespace for the generated code.</span></span> <span data-ttu-id="329b1-251">Przestrzeń nazw muszą być zgodne ze standardami CLR (na przykład, bez spacji i znaków ukośnik odwrotny).</span><span class="sxs-lookup"><span data-stu-id="329b1-251">The namespace must conform to CLR standards (for example, no spaces or backslash characters).</span></span>|  
|<span data-ttu-id="329b1-252">opcje</span><span class="sxs-lookup"><span data-stu-id="329b1-252">options</span></span>|<span data-ttu-id="329b1-253">Jedną z następujących wartości: `none`, `properties` (generuje właściwości zamiast pola publiczne), `order`, lub `enableDataBinding` (zobacz `/order` i `/enableDataBinding` przełączników w poprzedniej sekcji Opcje pliku XSD.</span><span class="sxs-lookup"><span data-stu-id="329b1-253">One of the following values: `none`, `properties` (generates properties instead of public fields), `order`, or `enableDataBinding` (see the `/order` and `/enableDataBinding` switches in the preceding XSD File Options section.</span></span>|  
  
 <span data-ttu-id="329b1-254">Można także kontrolować sposób `DataSet` kod został wygenerowany za pomocą `<generateDataSets\>` elementu.</span><span class="sxs-lookup"><span data-stu-id="329b1-254">You can also control how `DataSet` code is generated by using the `<generateDataSets\>` element.</span></span> <span data-ttu-id="329b1-255">Następujący kod XML określa, że wygenerowany codeuses `DataSet` struktury (takich jak <xref:System.Data.DataTable> klasy) do utworzenia kodu języka Visual Basic dla określonego elementu.</span><span class="sxs-lookup"><span data-stu-id="329b1-255">The following XML specifies that the generated codeuses `DataSet` structures (such as the <xref:System.Data.DataTable> class) to create Visual Basic code for a specified element.</span></span> <span data-ttu-id="329b1-256">Wygenerowany struktur zestawu danych będzie obsługiwać zapytań LINQ.</span><span class="sxs-lookup"><span data-stu-id="329b1-256">The generated DataSet structures will support LINQ queries.</span></span>  
  
 `<xsd xmlns='http://microsoft.com/dotnet/tools/xsd/'>`  
  
 `<generateDataSet language='VB' namespace='Microsoft.Serialization.Examples' enableLinqDataSet='true'>`  
  
 `</generateDataSet>`  
  
 `</xsd>`  
  
 <span data-ttu-id="329b1-257">Można ustawić dla opcji `<generateDataSet\>` obejmują elementu.</span><span class="sxs-lookup"><span data-stu-id="329b1-257">Options you can set for the `<generateDataSet\>` element include the following.</span></span>  
  
|<span data-ttu-id="329b1-258">Element</span><span class="sxs-lookup"><span data-stu-id="329b1-258">Element</span></span>|<span data-ttu-id="329b1-259">Opis</span><span class="sxs-lookup"><span data-stu-id="329b1-259">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="329b1-260">\<Schemat ></span><span class="sxs-lookup"><span data-stu-id="329b1-260">\<schema></span></span>|<span data-ttu-id="329b1-261">Określa PLik schematu XML do generowania kodu.</span><span class="sxs-lookup"><span data-stu-id="329b1-261">Specifies an XML Schema file to generate code for.</span></span> <span data-ttu-id="329b1-262">Wiele plików schematów XML można określić przy użyciu wielu \<schematu > elementów.</span><span class="sxs-lookup"><span data-stu-id="329b1-262">Multiple XML Schema files can be specified using multiple \<schema> elements.</span></span>|  
  
 <span data-ttu-id="329b1-263">Poniższa tabela zawiera atrybuty, które mogą być używane z `<generateDataSet\>` elementu.</span><span class="sxs-lookup"><span data-stu-id="329b1-263">The following table shows the attributes that can be used with the `<generateDataSet\>` element.</span></span>  
  
|<span data-ttu-id="329b1-264">Atrybut</span><span class="sxs-lookup"><span data-stu-id="329b1-264">Attribute</span></span>|<span data-ttu-id="329b1-265">Opis</span><span class="sxs-lookup"><span data-stu-id="329b1-265">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="329b1-266">enableLinqDataSet</span><span class="sxs-lookup"><span data-stu-id="329b1-266">enableLinqDataSet</span></span>|<span data-ttu-id="329b1-267">Określa, że wygenerowanego zestawu danych mogą być wyszukiwane względem przy użyciu LINQ do zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="329b1-267">Specifies that the generated DataSet can be queried against using LINQ to DataSet.</span></span> <span data-ttu-id="329b1-268">Wartość domyślna to false.</span><span class="sxs-lookup"><span data-stu-id="329b1-268">The default value is false.</span></span>|  
|<span data-ttu-id="329b1-269">język</span><span class="sxs-lookup"><span data-stu-id="329b1-269">language</span></span>|<span data-ttu-id="329b1-270">Określa język programowania.</span><span class="sxs-lookup"><span data-stu-id="329b1-270">Specifies the programming language to use.</span></span> <span data-ttu-id="329b1-271">Wybierz z `CS` (C#, wartość domyślna), `VB` (Visual Basic), `JS` (JScript) lub `VJS` (Visual J#).</span><span class="sxs-lookup"><span data-stu-id="329b1-271">Choose from `CS` (C#, the default), `VB` (Visual Basic), `JS` (JScript), or `VJS` (Visual J#).</span></span> <span data-ttu-id="329b1-272">Można również określić pełną nazwę klasy, która implementuje <xref:System.CodeDom.Compiler.CodeDomProvider>.</span><span class="sxs-lookup"><span data-stu-id="329b1-272">You can also specify a fully qualified name for a class that implements <xref:System.CodeDom.Compiler.CodeDomProvider>.</span></span>|  
|<span data-ttu-id="329b1-273">— przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="329b1-273">namespace</span></span>|<span data-ttu-id="329b1-274">Określa przestrzeń nazw dla wygenerowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="329b1-274">Specifies the namespace for the generated code.</span></span> <span data-ttu-id="329b1-275">Przestrzeń nazw muszą być zgodne ze standardami CLR (na przykład, bez spacji i znaków ukośnik odwrotny).</span><span class="sxs-lookup"><span data-stu-id="329b1-275">The namespace must conform to CLR standards (for example, no spaces or backslash characters).</span></span>|  
  
 <span data-ttu-id="329b1-276">Atrybuty, które mogą być ustawione na najwyższym poziomie są `<xsd\>` elementu.</span><span class="sxs-lookup"><span data-stu-id="329b1-276">There are attributes that you can set on the top level `<xsd\>` element.</span></span> <span data-ttu-id="329b1-277">Te opcje można użyć z żadnego z elementów podrzędnych (`<generateSchemas\>`, `<generateClasses\>` lub `<generateDataSet\>`).</span><span class="sxs-lookup"><span data-stu-id="329b1-277">These options can be used with any of the child elements (`<generateSchemas\>`, `<generateClasses\>` or `<generateDataSet\>`).</span></span> <span data-ttu-id="329b1-278">Poniższy kod XML generuje kod dla elementu o nazwie "IDItems" w katalogu wyjściowego o nazwie "MyOutputDirectory".</span><span class="sxs-lookup"><span data-stu-id="329b1-278">The following XML code generates code for an element named "IDItems" in the output directory named "MyOutputDirectory".</span></span>  
  
```xml  
<xsd xmlns='http://microsoft.com/dotnet/tools/xsd/' output='MyOutputDirectory'>  
<generateClasses>  
<element>IDItems</element>  
</generateClasses>  
</xsd>  
```  
  
 <span data-ttu-id="329b1-279">Poniższa tabela zawiera atrybuty, które umożliwia także z `\<xsd>` elementu.</span><span class="sxs-lookup"><span data-stu-id="329b1-279">The following table shows the attributes that can also be used with the `\<xsd>` element.</span></span>  
  
|<span data-ttu-id="329b1-280">Atrybut</span><span class="sxs-lookup"><span data-stu-id="329b1-280">Attribute</span></span>|<span data-ttu-id="329b1-281">Opis</span><span class="sxs-lookup"><span data-stu-id="329b1-281">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="329b1-282">dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="329b1-282">output</span></span>|<span data-ttu-id="329b1-283">Nazwa katalogu, w którym zostaną umieszczone wygenerowanego pliku schematu lub kodu.</span><span class="sxs-lookup"><span data-stu-id="329b1-283">The name of a directory where the generated schema or code file will be placed.</span></span>|  
|<span data-ttu-id="329b1-284">nologo</span><span class="sxs-lookup"><span data-stu-id="329b1-284">nologo</span></span>|<span data-ttu-id="329b1-285">Pomija transparentu.</span><span class="sxs-lookup"><span data-stu-id="329b1-285">Suppresses the banner.</span></span> <span data-ttu-id="329b1-286">Ustaw `true` lub `false`.</span><span class="sxs-lookup"><span data-stu-id="329b1-286">Set to `true` or `false`.</span></span>|  
|<span data-ttu-id="329b1-287">Pomoc</span><span class="sxs-lookup"><span data-stu-id="329b1-287">help</span></span>|<span data-ttu-id="329b1-288">Wyświetla składnię polecenia i opcje narzędzia.</span><span class="sxs-lookup"><span data-stu-id="329b1-288">Displays command syntax and options for the tool.</span></span> <span data-ttu-id="329b1-289">Ustaw `true` lub `false`.</span><span class="sxs-lookup"><span data-stu-id="329b1-289">Set to `true` or `false`.</span></span>|  
  
## <a name="examples"></a><span data-ttu-id="329b1-290">Przykłady</span><span class="sxs-lookup"><span data-stu-id="329b1-290">Examples</span></span>  
 <span data-ttu-id="329b1-291">Następujące polecenie generuje schematu XML z `myFile.xdr` i zapisuje go w bieżącym katalogu.</span><span class="sxs-lookup"><span data-stu-id="329b1-291">The following command generates an XML schema from `myFile.xdr` and saves it to the current directory.</span></span>  
  
```  
xsd myFile.xdr   
```  
  
 <span data-ttu-id="329b1-292">Następujące polecenie generuje schematu XML z `myFile.xml` i zapisuje go w określonym katalogu.</span><span class="sxs-lookup"><span data-stu-id="329b1-292">The following command generates an XML schema from `myFile.xml` and saves it to the specified directory.</span></span>  
  
```  
xsd myFile.xml /outputdir:myOutputDir  
```  
  
 <span data-ttu-id="329b1-293">Następujące polecenie generuje zestaw danych, który odpowiada określony schemat w języku C# i zapisuje je `XSDSchemaFile.cs` w bieżącym katalogu.</span><span class="sxs-lookup"><span data-stu-id="329b1-293">The following command generates a data set that corresponds to the specified schema in the C# language and saves it as `XSDSchemaFile.cs` in the current directory.</span></span>  
  
```  
xsd /dataset /language:CS XSDSchemaFile.xsd  
```  
  
 <span data-ttu-id="329b1-294">Następujące polecenie generuje schematów XML dla wszystkich typów w zestawie `myAssembly.dll` i zapisuje je jako `schema0.xsd` w bieżącym katalogu.</span><span class="sxs-lookup"><span data-stu-id="329b1-294">The following command generates XML schemas for all types in the assembly `myAssembly.dll` and saves them as `schema0.xsd` in the current directory.</span></span>  
  
```  
xsd myAssembly.dll    
```  
  
## <a name="see-also"></a><span data-ttu-id="329b1-295">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="329b1-295">See Also</span></span>  
 <xref:System.Data.DataSet>  
 <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>  
 <span data-ttu-id="329b1-296">[Narzędzia](../../../docs/framework/tools/index.md)    </span><span class="sxs-lookup"><span data-stu-id="329b1-296">[Tools](../../../docs/framework/tools/index.md)    </span></span>  
 [<span data-ttu-id="329b1-297">Wiersz polecenia</span><span class="sxs-lookup"><span data-stu-id="329b1-297">Command Prompts</span></span>](../../../docs/framework/tools/developer-command-prompt-for-vs.md)  
 [<span data-ttu-id="329b1-298">LINQ do DataSet — omówienie</span><span class="sxs-lookup"><span data-stu-id="329b1-298">LINQ to DataSet Overview</span></span>](../../../docs/framework/data/adonet/linq-to-dataset-overview.md)  
 [<span data-ttu-id="329b1-299">Wykonywanie zapytania Typizowane zbiory danych</span><span class="sxs-lookup"><span data-stu-id="329b1-299">Querying Typed DataSets</span></span>](../../../docs/framework/data/adonet/querying-typed-datasets.md)  
 [<span data-ttu-id="329b1-300">LINQ (zapytania o języku zintegrowanym)</span><span class="sxs-lookup"><span data-stu-id="329b1-300">LINQ (Language-Integrated Query)</span></span>](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)
