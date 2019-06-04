---
title: Przykład technologii serializacji z tolerancją wersji
ms.date: 03/30/2017
ms.assetid: 2a183664-bfbf-4ff0-96f6-c836284ea916
ms.openlocfilehash: 6c30c39848be02785b6b808ecf4af711c0c9e95d
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2019
ms.locfileid: "66482995"
---
# <a name="version-tolerant-serialization-technology-sample"></a><span data-ttu-id="6ce8f-102">Przykład technologii serializacji z tolerancją wersji</span><span class="sxs-lookup"><span data-stu-id="6ce8f-102">Version Tolerant Serialization Technology Sample</span></span>
[<span data-ttu-id="6ce8f-103">Pobierz przykładowe</span><span class="sxs-lookup"><span data-stu-id="6ce8f-103">Download Sample</span></span>](https://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Runtime%20Serialization/VTS.zip.exe)  
  
 <span data-ttu-id="6ce8f-104">W przykładzie pokazano funkcje tolerancja wersji programu .NET serializacji.</span><span class="sxs-lookup"><span data-stu-id="6ce8f-104">This sample demonstrates the version tolerance features of .NET Serialization.</span></span> <span data-ttu-id="6ce8f-105">Próbka tworzy aplikacje, które używają różnych wersji <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> do serializacji i deserializacji danych.</span><span class="sxs-lookup"><span data-stu-id="6ce8f-105">The sample builds applications that use different versions of a <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> to serialize and deserialize data.</span></span> <span data-ttu-id="6ce8f-106">Niezależnie od obecności wersje różnych typów aplikacji bezproblemowo łączy.</span><span class="sxs-lookup"><span data-stu-id="6ce8f-106">Despite the presence of different type versions, the applications communicate seamlessly.</span></span> <span data-ttu-id="6ce8f-107">Aby uzyskać więcej informacji, zobacz [serializacja z tolerancją wersji](../../../docs/standard/serialization/version-tolerant-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="6ce8f-107">For more information, see [Version Tolerant Serialization](../../../docs/standard/serialization/version-tolerant-serialization.md).</span></span>  
  
### <a name="to-build-the-sample-using-the-command-prompt"></a><span data-ttu-id="6ce8f-108">Aby skompilować przykład za pomocą wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="6ce8f-108">To build the sample using the command prompt</span></span>  
  
1. <span data-ttu-id="6ce8f-109">Otwórz okno wiersza polecenia i przejdź do jednej z podkatalogi specyficzny dla języka (w obszarze aplikację V1 lub V2) dla próbki.</span><span class="sxs-lookup"><span data-stu-id="6ce8f-109">Open a Command Prompt window and navigate to one of the language-specific subdirectories (under V1 Application or V2 Application) for the sample.</span></span>  
  
2. <span data-ttu-id="6ce8f-110">Typ **msbuild.exe \<ver > application.sln** w wierszu polecenia (gdzie \<serwerów > jest v1 lub v2).</span><span class="sxs-lookup"><span data-stu-id="6ce8f-110">Type **msbuild.exe \<ver> application.sln** at the command line (where \<ver> is either v1 or v2).</span></span>  
  
### <a name="to-build-the-sample-using-visual-studio"></a><span data-ttu-id="6ce8f-111">Aby skompilować przykład za pomocą programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="6ce8f-111">To build the sample using Visual Studio</span></span>  
  
1. <span data-ttu-id="6ce8f-112">Otwórz Eksplorator plików i przejdź do jednej z podkatalogi specyficzny dla języka dla próbki.</span><span class="sxs-lookup"><span data-stu-id="6ce8f-112">Open File Explorer and navigate to one of the language-specific subdirectories for the sample.</span></span>  
  
2. <span data-ttu-id="6ce8f-113">Przejdź do podkatalogu V1 aplikacji w katalogu, który został wybrany w poprzednim kroku.</span><span class="sxs-lookup"><span data-stu-id="6ce8f-113">Navigate to the V1 Application subdirectory of the directory you selected in the previous step.</span></span>  
  
3. <span data-ttu-id="6ce8f-114">Kliknij dwukrotnie ikonę Application.sln V1 do otwierania tego pliku w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6ce8f-114">Double-click the icon for V1 Application.sln to open the file in Visual Studio.</span></span>  
  
4. <span data-ttu-id="6ce8f-115">Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.</span><span class="sxs-lookup"><span data-stu-id="6ce8f-115">On the **Build** menu, click **Build Solution**.</span></span>  
  
5. <span data-ttu-id="6ce8f-116">Przejdź do podkatalogu aplikacji w wersji 2 i Powtórz dwa poprzednie kroki do tworzenia aplikacji w wersji 2.</span><span class="sxs-lookup"><span data-stu-id="6ce8f-116">Navigate to the V2 Application subdirectory and repeat the two previous steps to build the V2 Application.</span></span>  
  
 <span data-ttu-id="6ce8f-117">Aplikacje zostanie utworzona w domyślnych podkatalogów \bin lub \bin\Debug ich katalogów odpowiednich projektu.</span><span class="sxs-lookup"><span data-stu-id="6ce8f-117">The applications will be built in the default \bin or \bin\Debug subdirectories of their respective project directories.</span></span>  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="6ce8f-118">Aby uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="6ce8f-118">To run the sample</span></span>  
  
1. <span data-ttu-id="6ce8f-119">W oknie wiersza polecenia przejdź do wybranego podczas tworzenia aplikacji przykładowych podkatalogu specyficzny dla języka.</span><span class="sxs-lookup"><span data-stu-id="6ce8f-119">In the Command Prompt window, navigate to the language-specific subdirectory that you selected when you built the sample applications.</span></span>  
  
2. <span data-ttu-id="6ce8f-120">Typ **runme.cmd** w wierszu polecenia do uruchamiania obu aplikacji jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="6ce8f-120">Type **runme.cmd** at the command line to run both applications at once.</span></span>  
  
 <span data-ttu-id="6ce8f-121">Ewentualnie przejdź do katalogi, które zawierają nowe PLiki wykonywalne i uruchom je sekwencyjnie.</span><span class="sxs-lookup"><span data-stu-id="6ce8f-121">Alternatively, navigate to the directories that contain the new executables and run them sequentially.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6ce8f-122">Próbka tworzy aplikacji konsoli.</span><span class="sxs-lookup"><span data-stu-id="6ce8f-122">The sample builds console applications.</span></span> <span data-ttu-id="6ce8f-123">Należy uruchomić i uruchom je w oknie wiersza polecenia, aby wyświetlić ich danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="6ce8f-123">You must launch and run them in a Command Prompt window to view their output.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ce8f-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6ce8f-124">See also</span></span>

- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>
- <xref:System.IO.FileStream>
