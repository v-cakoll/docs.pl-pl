---
title: Przykład technologii serializacji z tolerancją wersji
ms.date: 03/30/2017
ms.assetid: 2a183664-bfbf-4ff0-96f6-c836284ea916
ms.openlocfilehash: 317a47d46b839417e01eed9deca2459a96aaa201
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960776"
---
# <a name="version-tolerant-serialization-technology-sample"></a><span data-ttu-id="03c32-102">Przykład technologii serializacji z tolerancją wersji</span><span class="sxs-lookup"><span data-stu-id="03c32-102">Version Tolerant Serialization Technology Sample</span></span>
[<span data-ttu-id="03c32-103">Pobierz przykład</span><span class="sxs-lookup"><span data-stu-id="03c32-103">Download Sample</span></span>](https://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Runtime%20Serialization/VTS.zip.exe)  
  
 <span data-ttu-id="03c32-104">Ten przykład ilustruje funkcję tolerancji wersji serializacji platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="03c32-104">This sample demonstrates the version tolerance features of .NET Serialization.</span></span> <span data-ttu-id="03c32-105">Przykład tworzy aplikacje, które używają różnych wersji programu, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> do serializacji i deserializacji danych.</span><span class="sxs-lookup"><span data-stu-id="03c32-105">The sample builds applications that use different versions of a <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> to serialize and deserialize data.</span></span> <span data-ttu-id="03c32-106">Mimo obecności różnych wersji typu, aplikacje komunikują się bezproblemowo.</span><span class="sxs-lookup"><span data-stu-id="03c32-106">Despite the presence of different type versions, the applications communicate seamlessly.</span></span> <span data-ttu-id="03c32-107">Aby uzyskać więcej informacji, zobacz [Serializacja odporna na wersje](../../../docs/standard/serialization/version-tolerant-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="03c32-107">For more information, see [Version Tolerant Serialization](../../../docs/standard/serialization/version-tolerant-serialization.md).</span></span>  
  
### <a name="to-build-the-sample-using-the-command-prompt"></a><span data-ttu-id="03c32-108">Aby skompilować przykład za pomocą wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="03c32-108">To build the sample using the command prompt</span></span>  
  
1. <span data-ttu-id="03c32-109">Otwórz okno wiersza polecenia i przejdź do jednego z podkatalogów specyficznych dla języka (w aplikacji v1 lub v2) dla przykładu.</span><span class="sxs-lookup"><span data-stu-id="03c32-109">Open a Command Prompt window and navigate to one of the language-specific subdirectories (under V1 Application or V2 Application) for the sample.</span></span>  
  
2. <span data-ttu-id="03c32-110">Wpisz **MSBuild. exe \<Ver> Application. sln** w wierszu polecenia (gdzie \<Ver> ma wartość v1 lub v2).</span><span class="sxs-lookup"><span data-stu-id="03c32-110">Type **msbuild.exe \<ver> application.sln** at the command line (where \<ver> is either v1 or v2).</span></span>  
  
### <a name="to-build-the-sample-using-visual-studio"></a><span data-ttu-id="03c32-111">Aby skompilować przykład za pomocą programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="03c32-111">To build the sample using Visual Studio</span></span>  
  
1. <span data-ttu-id="03c32-112">Otwórz Eksploratora plików i przejdź do jednego z podkatalogów właściwych dla języka dla przykładu.</span><span class="sxs-lookup"><span data-stu-id="03c32-112">Open File Explorer and navigate to one of the language-specific subdirectories for the sample.</span></span>  
  
2. <span data-ttu-id="03c32-113">Przejdź do podkatalogu aplikacji w wersji 1 katalogu, który został wybrany w poprzednim kroku.</span><span class="sxs-lookup"><span data-stu-id="03c32-113">Navigate to the V1 Application subdirectory of the directory you selected in the previous step.</span></span>  
  
3. <span data-ttu-id="03c32-114">Kliknij dwukrotnie ikonę aplikacji v1. sln, aby otworzyć plik w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="03c32-114">Double-click the icon for V1 Application.sln to open the file in Visual Studio.</span></span>  
  
4. <span data-ttu-id="03c32-115">W menu **Kompilacja** kliknij pozycję **Kompiluj rozwiązanie**.</span><span class="sxs-lookup"><span data-stu-id="03c32-115">On the **Build** menu, click **Build Solution**.</span></span>  
  
5. <span data-ttu-id="03c32-116">Przejdź do podkatalogu aplikacji w wersji 2 i Powtórz dwa poprzednie kroki w celu skompilowania aplikacji w wersji 2.</span><span class="sxs-lookup"><span data-stu-id="03c32-116">Navigate to the V2 Application subdirectory and repeat the two previous steps to build the V2 Application.</span></span>  
  
 <span data-ttu-id="03c32-117">Aplikacje zostaną skompilowane w domyślnych podkatalogach \Bin lub \bin\Debug odpowiednich katalogów projektu.</span><span class="sxs-lookup"><span data-stu-id="03c32-117">The applications will be built in the default \bin or \bin\Debug subdirectories of their respective project directories.</span></span>  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="03c32-118">Aby uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="03c32-118">To run the sample</span></span>  
  
1. <span data-ttu-id="03c32-119">W oknie wiersza polecenia przejdź do podkatalogu specyficznego dla języka, który został wybrany podczas tworzenia przykładowych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="03c32-119">In the Command Prompt window, navigate to the language-specific subdirectory that you selected when you built the sample applications.</span></span>  
  
2. <span data-ttu-id="03c32-120">Wpisz **RUNME. cmd** w wierszu polecenia, aby uruchomić oba aplikacje jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="03c32-120">Type **runme.cmd** at the command line to run both applications at once.</span></span>  
  
 <span data-ttu-id="03c32-121">Ewentualnie przejdź do katalogi, które zawierają nowe PLiki wykonywalne i uruchom je sekwencyjnie.</span><span class="sxs-lookup"><span data-stu-id="03c32-121">Alternatively, navigate to the directories that contain the new executables and run them sequentially.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="03c32-122">Przykład tworzy aplikacje konsolowe.</span><span class="sxs-lookup"><span data-stu-id="03c32-122">The sample builds console applications.</span></span> <span data-ttu-id="03c32-123">Należy uruchomić i uruchom je w oknie wiersza polecenia, aby wyświetlić ich danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="03c32-123">You must launch and run them in a Command Prompt window to view their output.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03c32-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="03c32-124">See also</span></span>

- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>
- <xref:System.IO.FileStream>
