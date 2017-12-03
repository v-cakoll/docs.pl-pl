---
title: "Przykładowe technologii serializacji z tolerancją dla wersji"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2a183664-bfbf-4ff0-96f6-c836284ea916
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bde508f6fd578050501f95f2f9316c6c458017de
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="version-tolerant-serialization-technology-sample"></a><span data-ttu-id="e0d8d-102">Przykładowe technologii serializacji z tolerancją dla wersji</span><span class="sxs-lookup"><span data-stu-id="e0d8d-102">Version Tolerant Serialization Technology Sample</span></span>
[<span data-ttu-id="e0d8d-103">Pobieranie próbki</span><span class="sxs-lookup"><span data-stu-id="e0d8d-103">Download Sample</span></span>](http://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Runtime%20Serialization/VTS.zip.exe)  
  
 <span data-ttu-id="e0d8d-104">W przykładzie pokazano funkcje tolerancji wersji serializacji .NET.</span><span class="sxs-lookup"><span data-stu-id="e0d8d-104">This sample demonstrates the version tolerance features of .NET Serialization.</span></span> <span data-ttu-id="e0d8d-105">Próbka tworzy aplikacje używające różnych wersji <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> do serializowania i deserializowania danych.</span><span class="sxs-lookup"><span data-stu-id="e0d8d-105">The sample builds applications that use different versions of a <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> to serialize and deserialize data.</span></span> <span data-ttu-id="e0d8d-106">Niezależnie od obecności innego typu wersji aplikacji komunikują się bezproblemowo.</span><span class="sxs-lookup"><span data-stu-id="e0d8d-106">Despite the presence of different type versions, the applications communicate seamlessly.</span></span> <span data-ttu-id="e0d8d-107">Aby uzyskać więcej informacji, zobacz [serializacji z tolerancją dla wersji](../../../docs/standard/serialization/version-tolerant-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="e0d8d-107">For more information, see [Version Tolerant Serialization](../../../docs/standard/serialization/version-tolerant-serialization.md).</span></span>  
  
### <a name="to-build-the-sample-using-the-command-prompt"></a><span data-ttu-id="e0d8d-108">Aby samodzielnie tworzyć przykładowy przy użyciu wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="e0d8d-108">To build the sample using the command prompt</span></span>  
  
1.  <span data-ttu-id="e0d8d-109">Otwórz okno wiersza polecenia i przejdź do jednej z podkatalogi specyficzne dla języka (w obszarze aplikację V1 lub V2) przykładowej.</span><span class="sxs-lookup"><span data-stu-id="e0d8d-109">Open a Command Prompt window and navigate to one of the language-specific subdirectories (under V1 Application or V2 Application) for the sample.</span></span>  
  
2.  <span data-ttu-id="e0d8d-110">Typ **msbuild.exe \<ver > application.sln** w wierszu polecenia (gdzie \<ver > jest v1 lub v2).</span><span class="sxs-lookup"><span data-stu-id="e0d8d-110">Type **msbuild.exe \<ver> application.sln** at the command line (where \<ver> is either v1 or v2).</span></span>  
  
### <a name="to-build-the-sample-using-visual-studio"></a><span data-ttu-id="e0d8d-111">Aby samodzielnie tworzyć przykładowy przy użyciu programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e0d8d-111">To build the sample using Visual Studio</span></span>  
  
1.  <span data-ttu-id="e0d8d-112">Otwórz [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] i przejdź do jednej z przykładowej podkatalogi specyficzny dla języka.</span><span class="sxs-lookup"><span data-stu-id="e0d8d-112">Open [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] and navigate to one of the language-specific subdirectories for the sample.</span></span>  
  
2.  <span data-ttu-id="e0d8d-113">Przejdź do podkatalogu V1 aplikacji katalogu, który wybrano w poprzednim kroku.</span><span class="sxs-lookup"><span data-stu-id="e0d8d-113">Navigate to the V1 Application subdirectory of the directory you selected in the previous step.</span></span>  
  
3.  <span data-ttu-id="e0d8d-114">Kliknij dwukrotnie ikonę Application.sln V1 otworzyć plik w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e0d8d-114">Double-click the icon for V1 Application.sln to open the file in Visual Studio.</span></span>  
  
4.  <span data-ttu-id="e0d8d-115">Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.</span><span class="sxs-lookup"><span data-stu-id="e0d8d-115">On the **Build** menu, click **Build Solution**.</span></span>  
  
5.  <span data-ttu-id="e0d8d-116">Przejdź do podkatalogu aplikacji V2 i Powtórz dwa poprzednie kroki, aby skompilować aplikację V2.</span><span class="sxs-lookup"><span data-stu-id="e0d8d-116">Navigate to the V2 Application subdirectory and repeat the two previous steps to build the V2 Application.</span></span>  
  
 <span data-ttu-id="e0d8d-117">Aplikacje zostaną skompilowane w podkatalogach \bin lub \bin\Debug domyślne katalogi ich odpowiednich projektu.</span><span class="sxs-lookup"><span data-stu-id="e0d8d-117">The applications will be built in the default \bin or \bin\Debug subdirectories of their respective project directories.</span></span>  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="e0d8d-118">Aby uruchomić przykładowy</span><span class="sxs-lookup"><span data-stu-id="e0d8d-118">To run the sample</span></span>  
  
1.  <span data-ttu-id="e0d8d-119">W oknie wiersza polecenia przejdź do podkatalogu specyficzny dla języka wybranego podczas tworzenia aplikacji przykładowej.</span><span class="sxs-lookup"><span data-stu-id="e0d8d-119">In the Command Prompt window, navigate to the language-specific subdirectory that you selected when you built the sample applications.</span></span>  
  
2.  <span data-ttu-id="e0d8d-120">Typ **runme.cmd** w wierszu polecenia, aby uruchomić jednocześnie obydwu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e0d8d-120">Type **runme.cmd** at the command line to run both applications at once.</span></span>  
  
 <span data-ttu-id="e0d8d-121">Ewentualnie przejdź do katalogi, które zawierają nowe PLiki wykonywalne i uruchom je sekwencyjnie.</span><span class="sxs-lookup"><span data-stu-id="e0d8d-121">Alternatively, navigate to the directories that contain the new executables and run them sequentially.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e0d8d-122">Przykład tworzy aplikacji konsoli.</span><span class="sxs-lookup"><span data-stu-id="e0d8d-122">The sample builds console applications.</span></span> <span data-ttu-id="e0d8d-123">Należy uruchomić i uruchom je w oknie wiersza polecenia, aby wyświetlić ich danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="e0d8d-123">You must launch and run them in a Command Prompt window to view their output.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0d8d-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e0d8d-124">See Also</span></span>  
 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>  
 <xref:System.IO.FileStream>
