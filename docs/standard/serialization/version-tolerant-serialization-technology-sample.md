---
title: Przykładowe technologii serializacji z tolerancją dla wersji
ms.date: 03/30/2017
ms.assetid: 2a183664-bfbf-4ff0-96f6-c836284ea916
ms.openlocfilehash: 996c041cd85551124fe62086e4894709183798d8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="version-tolerant-serialization-technology-sample"></a><span data-ttu-id="0ef20-102">Przykładowe technologii serializacji z tolerancją dla wersji</span><span class="sxs-lookup"><span data-stu-id="0ef20-102">Version Tolerant Serialization Technology Sample</span></span>
[<span data-ttu-id="0ef20-103">Pobieranie próbki</span><span class="sxs-lookup"><span data-stu-id="0ef20-103">Download Sample</span></span>](https://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Runtime%20Serialization/VTS.zip.exe)  
  
 <span data-ttu-id="0ef20-104">W przykładzie pokazano funkcje tolerancji wersji serializacji .NET.</span><span class="sxs-lookup"><span data-stu-id="0ef20-104">This sample demonstrates the version tolerance features of .NET Serialization.</span></span> <span data-ttu-id="0ef20-105">Próbka tworzy aplikacje używające różnych wersji <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> do serializowania i deserializowania danych.</span><span class="sxs-lookup"><span data-stu-id="0ef20-105">The sample builds applications that use different versions of a <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> to serialize and deserialize data.</span></span> <span data-ttu-id="0ef20-106">Niezależnie od obecności innego typu wersji aplikacji komunikują się bezproblemowo.</span><span class="sxs-lookup"><span data-stu-id="0ef20-106">Despite the presence of different type versions, the applications communicate seamlessly.</span></span> <span data-ttu-id="0ef20-107">Aby uzyskać więcej informacji, zobacz [serializacji z tolerancją dla wersji](../../../docs/standard/serialization/version-tolerant-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="0ef20-107">For more information, see [Version Tolerant Serialization](../../../docs/standard/serialization/version-tolerant-serialization.md).</span></span>  
  
### <a name="to-build-the-sample-using-the-command-prompt"></a><span data-ttu-id="0ef20-108">Aby samodzielnie tworzyć przykładowy przy użyciu wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="0ef20-108">To build the sample using the command prompt</span></span>  
  
1.  <span data-ttu-id="0ef20-109">Otwórz okno wiersza polecenia i przejdź do jednej z podkatalogi specyficzne dla języka (w obszarze aplikację V1 lub V2) przykładowej.</span><span class="sxs-lookup"><span data-stu-id="0ef20-109">Open a Command Prompt window and navigate to one of the language-specific subdirectories (under V1 Application or V2 Application) for the sample.</span></span>  
  
2.  <span data-ttu-id="0ef20-110">Typ **msbuild.exe \<ver > application.sln** w wierszu polecenia (gdzie \<ver > jest v1 lub v2).</span><span class="sxs-lookup"><span data-stu-id="0ef20-110">Type **msbuild.exe \<ver> application.sln** at the command line (where \<ver> is either v1 or v2).</span></span>  
  
### <a name="to-build-the-sample-using-visual-studio"></a><span data-ttu-id="0ef20-111">Aby samodzielnie tworzyć przykładowy przy użyciu programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="0ef20-111">To build the sample using Visual Studio</span></span>  
  
1.  <span data-ttu-id="0ef20-112">Otwórz [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] i przejdź do jednej z przykładowej podkatalogi specyficzny dla języka.</span><span class="sxs-lookup"><span data-stu-id="0ef20-112">Open [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] and navigate to one of the language-specific subdirectories for the sample.</span></span>  
  
2.  <span data-ttu-id="0ef20-113">Przejdź do podkatalogu V1 aplikacji katalogu, który wybrano w poprzednim kroku.</span><span class="sxs-lookup"><span data-stu-id="0ef20-113">Navigate to the V1 Application subdirectory of the directory you selected in the previous step.</span></span>  
  
3.  <span data-ttu-id="0ef20-114">Kliknij dwukrotnie ikonę Application.sln V1 otworzyć plik w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0ef20-114">Double-click the icon for V1 Application.sln to open the file in Visual Studio.</span></span>  
  
4.  <span data-ttu-id="0ef20-115">Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.</span><span class="sxs-lookup"><span data-stu-id="0ef20-115">On the **Build** menu, click **Build Solution**.</span></span>  
  
5.  <span data-ttu-id="0ef20-116">Przejdź do podkatalogu aplikacji V2 i Powtórz dwa poprzednie kroki, aby skompilować aplikację V2.</span><span class="sxs-lookup"><span data-stu-id="0ef20-116">Navigate to the V2 Application subdirectory and repeat the two previous steps to build the V2 Application.</span></span>  
  
 <span data-ttu-id="0ef20-117">Aplikacje zostaną skompilowane w podkatalogach \bin lub \bin\Debug domyślne katalogi ich odpowiednich projektu.</span><span class="sxs-lookup"><span data-stu-id="0ef20-117">The applications will be built in the default \bin or \bin\Debug subdirectories of their respective project directories.</span></span>  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="0ef20-118">Aby uruchomić przykładowy</span><span class="sxs-lookup"><span data-stu-id="0ef20-118">To run the sample</span></span>  
  
1.  <span data-ttu-id="0ef20-119">W oknie wiersza polecenia przejdź do podkatalogu specyficzny dla języka wybranego podczas tworzenia aplikacji przykładowej.</span><span class="sxs-lookup"><span data-stu-id="0ef20-119">In the Command Prompt window, navigate to the language-specific subdirectory that you selected when you built the sample applications.</span></span>  
  
2.  <span data-ttu-id="0ef20-120">Typ **runme.cmd** w wierszu polecenia, aby uruchomić jednocześnie obydwu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0ef20-120">Type **runme.cmd** at the command line to run both applications at once.</span></span>  
  
 <span data-ttu-id="0ef20-121">Ewentualnie przejdź do katalogi, które zawierają nowe PLiki wykonywalne i uruchom je sekwencyjnie.</span><span class="sxs-lookup"><span data-stu-id="0ef20-121">Alternatively, navigate to the directories that contain the new executables and run them sequentially.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0ef20-122">Przykład tworzy aplikacji konsoli.</span><span class="sxs-lookup"><span data-stu-id="0ef20-122">The sample builds console applications.</span></span> <span data-ttu-id="0ef20-123">Należy uruchomić i uruchom je w oknie wiersza polecenia, aby wyświetlić ich danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="0ef20-123">You must launch and run them in a Command Prompt window to view their output.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ef20-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0ef20-124">See Also</span></span>  
 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>  
 <xref:System.IO.FileStream>
