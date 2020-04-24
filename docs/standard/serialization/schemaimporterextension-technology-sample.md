---
title: Przykład technologii SchemaImporterExtension
ms.date: 03/30/2017
ms.assetid: 3f5eb78f-0ef6-433a-b095-3a63b1ce0bc9
ms.openlocfilehash: d63461425fd0b3366d39892512577b0dd706de13
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490868"
---
# <a name="schemaimporterextension-technology-sample"></a><span data-ttu-id="cb712-102">Przykład technologii SchemaImporterExtension</span><span class="sxs-lookup"><span data-stu-id="cb712-102">SchemaImporterExtension Technology Sample</span></span>
[<span data-ttu-id="cb712-103">Pobierz przykład</span><span class="sxs-lookup"><span data-stu-id="cb712-103">Download Sample</span></span>](https://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Xml%20Serialization/SchemaImporterExtension.zip.exe)  
  
 <span data-ttu-id="cb712-104">Ten przykład pokazuje niestandardowy <xref:System.Xml.Serialization.Advanced.SchemaImporterExtension> , który umożliwia precyzyjne sterowanie generowaniem kodu podczas importowania schematu XML.</span><span class="sxs-lookup"><span data-stu-id="cb712-104">This sample demonstrates a custom <xref:System.Xml.Serialization.Advanced.SchemaImporterExtension> that allows fine control over code generation when an XML schema is imported.</span></span> <span data-ttu-id="cb712-105">Aplikacja pokazuje, jak skompilować, zarejestrować i wywołać to rozszerzenie.</span><span class="sxs-lookup"><span data-stu-id="cb712-105">The application shows how to build, register and invoke this extension.</span></span>  
  
### <a name="to-build-the-sample-using-the-command-prompt"></a><span data-ttu-id="cb712-106">Aby skompilować przykład za pomocą wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="cb712-106">To build the sample using the command prompt</span></span>  
  
1. <span data-ttu-id="cb712-107">Otwórz okno wiersza polecenia i przejdź do jednego z podkatalogów właściwych dla języka dla przykładu.</span><span class="sxs-lookup"><span data-stu-id="cb712-107">Open a Command Prompt window and navigate to one of the language-specific subdirectories for the sample.</span></span>  
  
2. <span data-ttu-id="cb712-108">Wpisz **MSBuild. exe OrderSchemaImporterExtension. sln** w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="cb712-108">Type **msbuild.exe OrderSchemaImporterExtension.sln** at the command line.</span></span>  
  
### <a name="to-build-the-sample-using-visual-studio"></a><span data-ttu-id="cb712-109">Aby skompilować przykład za pomocą programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="cb712-109">To build the sample using Visual Studio</span></span>  
  
1. <span data-ttu-id="cb712-110">Otwórz Eksploratora plików i przejdź do jednego z podkatalogów właściwych dla języka dla przykładu.</span><span class="sxs-lookup"><span data-stu-id="cb712-110">Open File Explorer and navigate to one of the language-specific subdirectories for the sample.</span></span>  
  
2. <span data-ttu-id="cb712-111">Kliknij dwukrotnie ikonę OrderSchemaImporterExtension.sln do otwierania tego PLiku w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="cb712-111">Double-click the icon for OrderSchemaImporterExtension.sln to open the file in Visual Studio.</span></span>  
  
3. <span data-ttu-id="cb712-112">W menu **Kompilacja** kliknij pozycję **Kompiluj rozwiązanie**.</span><span class="sxs-lookup"><span data-stu-id="cb712-112">On the **Build** menu, click **Build Solution**.</span></span>  
  
 <span data-ttu-id="cb712-113">Aplikacja zostanie skompilowana w domyślnym katalogu \Bin lub \bin\Debug.</span><span class="sxs-lookup"><span data-stu-id="cb712-113">The application will be built in the default \bin or \bin\Debug directory.</span></span>  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="cb712-114">Aby uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="cb712-114">To run the sample</span></span>  
  
1. <span data-ttu-id="cb712-115">Przejdź do katalogu zawierającego nowy PLik wykonywalny, za pomocą wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="cb712-115">Navigate to the directory containing the new executable, using the command prompt.</span></span>  
  
2. <span data-ttu-id="cb712-116">Wpisz **[nazwa exe]** w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="cb712-116">Type **[exe name]** at the command line.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cb712-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cb712-117">Remarks</span></span>  
 <span data-ttu-id="cb712-118">Aby uzyskać więcej informacji na temat tworzenia przykładowych danych binarnych i kroków rejestracji, zobacz komentarze w plikach kodu źródłowego i Build. proj.</span><span class="sxs-lookup"><span data-stu-id="cb712-118">For more information about sample binary creation and registration steps, see the comments in the source code and build.proj files.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb712-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cb712-119">See also</span></span>

- <xref:System.CodeDom.CodeCompileUnit>
- <xref:System.CodeDom.CodeNamespace>
- <xref:System.CodeDom.CodeNamespaceImport>
- <xref:Microsoft.CSharp.CSharpCodeProvider>
- <xref:System.Xml.Serialization.IXmlSerializable>
- <xref:System.Xml.Serialization.Advanced.SchemaImporterExtension>
- <xref:System.CodeDom>
- <xref:System.CodeDom.Compiler>
- <xref:System.Web.Services.Description>
- <xref:System.Web.Services.Discovery>
- <xref:System.Xml.Serialization>
- <xref:System.Uri>
- <xref:Microsoft.VisualBasic.VBCodeProvider>
- <xref:System.Web.Services.Description.WebReference>
- <xref:System.Xml.Serialization.XmlSchemaImporter>
