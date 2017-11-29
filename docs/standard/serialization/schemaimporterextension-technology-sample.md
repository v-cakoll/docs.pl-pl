---
title: "Przykładowy element SchemaImporterExtension technologii"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3f5eb78f-0ef6-433a-b095-3a63b1ce0bc9
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 68e89053d1d4a36a0f015ed4e0082ae88e1de6a8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="schemaimporterextension-technology-sample"></a><span data-ttu-id="b282c-102">Przykładowy element SchemaImporterExtension technologii</span><span class="sxs-lookup"><span data-stu-id="b282c-102">SchemaImporterExtension Technology Sample</span></span>
[<span data-ttu-id="b282c-103">Pobieranie próbki</span><span class="sxs-lookup"><span data-stu-id="b282c-103">Download Sample</span></span>](http://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Xml%20Serialization/SchemaImporterExtension.zip.exe)  
  
 <span data-ttu-id="b282c-104">W tym przykładzie pokazano niestandardowego <xref:System.Xml.Serialization.Advanced.SchemaImporterExtension> który umożliwia szczegółową kontrolę generowania kodu podczas importowania schematu XML.</span><span class="sxs-lookup"><span data-stu-id="b282c-104">This sample demonstrates a custom <xref:System.Xml.Serialization.Advanced.SchemaImporterExtension> that allows fine control over code generation when an XML schema is imported.</span></span> <span data-ttu-id="b282c-105">Aplikacja pokazuje, jak do kompilacji, rejestrowania i wywołanie tego rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="b282c-105">The application shows how to build, register and invoke this extension.</span></span>  
  
### <a name="to-build-the-sample-using-the-command-prompt"></a><span data-ttu-id="b282c-106">Aby samodzielnie tworzyć przykładowy przy użyciu wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="b282c-106">To build the sample using the command prompt</span></span>  
  
1.  <span data-ttu-id="b282c-107">Otwórz okno wiersza polecenia i przejdź do jednej z przykładowej podkatalogi specyficzny dla języka.</span><span class="sxs-lookup"><span data-stu-id="b282c-107">Open a Command Prompt window and navigate to one of the language-specific subdirectories for the sample.</span></span>  
  
2.  <span data-ttu-id="b282c-108">Typ **msbuild.exe OrderSchemaImporterExtension.sln** w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="b282c-108">Type **msbuild.exe OrderSchemaImporterExtension.sln** at the command line.</span></span>  
  
### <a name="to-build-the-sample-using-visual-studio"></a><span data-ttu-id="b282c-109">Aby samodzielnie tworzyć przykładowy przy użyciu programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b282c-109">To build the sample using Visual Studio</span></span>  
  
1.  <span data-ttu-id="b282c-110">Otwórz [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] i przejdź do jednej z przykładowej podkatalogi specyficzny dla języka.</span><span class="sxs-lookup"><span data-stu-id="b282c-110">Open [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] and navigate to one of the language-specific subdirectories for the sample.</span></span>  
  
2.  <span data-ttu-id="b282c-111">Kliknij dwukrotnie ikonę OrderSchemaImporterExtension.sln do otwierania tego PLiku w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b282c-111">Double-click the icon for OrderSchemaImporterExtension.sln to open the file in Visual Studio.</span></span>  
  
3.  <span data-ttu-id="b282c-112">Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.</span><span class="sxs-lookup"><span data-stu-id="b282c-112">On the **Build** menu, click **Build Solution**.</span></span>  
  
 <span data-ttu-id="b282c-113">Aplikacja zostanie utworzona w domyślnym katalogu \bin lub \bin\Debug.</span><span class="sxs-lookup"><span data-stu-id="b282c-113">The application will be built in the default \bin or \bin\Debug directory.</span></span>  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="b282c-114">Aby uruchomić przykładowy</span><span class="sxs-lookup"><span data-stu-id="b282c-114">To run the sample</span></span>  
  
1.  <span data-ttu-id="b282c-115">Przejdź do katalogu zawierającego nowy PLik wykonywalny, za pomocą wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="b282c-115">Navigate to the directory containing the new executable, using the command prompt.</span></span>  
  
2.  <span data-ttu-id="b282c-116">Typ **[nazwa pliku exe]** w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="b282c-116">Type **[exe name]** at the command line.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b282c-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b282c-117">Remarks</span></span>  
 <span data-ttu-id="b282c-118">Aby uzyskać więcej informacji dotyczących tworzenia binarne próbki i kroki rejestracji Zobacz komentarze w kodzie i build.proj plikach źródłowych.</span><span class="sxs-lookup"><span data-stu-id="b282c-118">For more information about sample binary creation and registration steps, see the comments in the source code and build.proj files.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b282c-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b282c-119">See Also</span></span>  
 <xref:System.CodeDom.CodeCompileUnit>  
 <xref:System.CodeDom.CodeNamespace>  
 <xref:System.CodeDom.CodeNamespaceImport>  
 <xref:Microsoft.CSharp.CSharpCodeProvider>  
 <xref:System.Xml.Serialization.IXmlSerializable>  
 <xref:System.Xml.Serialization.Advanced.SchemaImporterExtension>  
 <xref:System.CodeDom>  
 <xref:System.CodeDom.Compiler>  
 <xref:System.Web.Services.Description>  
 <xref:System.Web.Services.Discovery>  
 <xref:System.Xml.Serialization>  
 <xref:System.Uri>  
 <xref:Microsoft.VisualBasic.VBCodeProvider>  
 <xref:System.Web.Services.Description.WebReference>  
 <xref:System.Xml.Serialization.XmlSchemaImporter>
