---
title: Pobieranie pakietu programu obsługi tokenów sieci Web JSON
ms.date: 10/10/2018
ms.assetid: d12b3f5b-f1f1-4a9d-a159-0c13e5976c90
ms.openlocfilehash: a8685a71d46778d932595965f32c0041b176bd83
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65633525"
---
# <a name="download-the-json-web-token-handler-package"></a><span data-ttu-id="098a4-102">Pobieranie pakietu programu obsługi tokenów Web JSON</span><span class="sxs-lookup"><span data-stu-id="098a4-102">Download the JSON Web Token Handler Package</span></span>

<span data-ttu-id="098a4-103">W tym temacie omówiono sposób pobierania i używania programu obsługi tokenów Web JSON w projekcie.</span><span class="sxs-lookup"><span data-stu-id="098a4-103">This topic discusses how to download and use the JSON Web Token Handler in your project.</span></span>

<span data-ttu-id="098a4-104">Rozszerzenie JSON Web Token Handler jest dostępne jako pakiet NuGet, który dodaje niezbędne zespoły i odwołania do projektu.</span><span class="sxs-lookup"><span data-stu-id="098a4-104">The JSON Web Token Handler extension is available as a NuGet package, which adds the necessary assemblies and references to your project.</span></span> <span data-ttu-id="098a4-105">Jeśli nie masz jeszcze zainstalowanego Menedżera NuGet, przejdź do strony [nuget.org](https://nuget.org) go zainstalować.</span><span class="sxs-lookup"><span data-stu-id="098a4-105">If you do not already have NuGet installed, go to [nuget.org](https://nuget.org) to install it.</span></span> <span data-ttu-id="098a4-106">Można wyświetlić historię wersji rozszerzenia odwiedzając jego stronę na NuGet: [JSON Web Token Handler dla narzędzia NuGet](https://www.nuget.org/packages/System.IdentityModel.Tokens.Jwt/)</span><span class="sxs-lookup"><span data-stu-id="098a4-106">You can see the versioning history for the extension by visiting its page on NuGet: [JSON Web Token Handler on NuGet](https://www.nuget.org/packages/System.IdentityModel.Tokens.Jwt/)</span></span>

## <a name="use-the-package-manager-gui"></a><span data-ttu-id="098a4-107">Użyj Menedżera pakietów GUI</span><span class="sxs-lookup"><span data-stu-id="098a4-107">Use the Package Manager GUI</span></span>

1. <span data-ttu-id="098a4-108">W programie Visual Studio, kliknij prawym przyciskiem myszy projekt w **Eksploratora rozwiązań**, a następnie wybierz pozycję **Zarządzaj pakietami NuGet**.</span><span class="sxs-lookup"><span data-stu-id="098a4-108">In Visual Studio, right-click your project in **Solution Explorer**, and then select **Manage NuGet Packages**.</span></span>

2. <span data-ttu-id="098a4-109">W **Zarządzaj pakietami NuGet** okna, kliknij pole wyszukiwania i wprowadź `JWT Token Handler` i naciśnij klawisz **Enter**.</span><span class="sxs-lookup"><span data-stu-id="098a4-109">In the **Manage NuGet Packages** window, click the search box and enter `JWT Token Handler` and press **Enter**.</span></span>

3. <span data-ttu-id="098a4-110">W okienku wyników kliknij **zainstalować** przycisku dla pierwszego wyniku.</span><span class="sxs-lookup"><span data-stu-id="098a4-110">From the results pane, click the **Install** button for the first result.</span></span>

4. <span data-ttu-id="098a4-111">Pakiet rozpocznie się pobieranie.</span><span class="sxs-lookup"><span data-stu-id="098a4-111">The package will begin downloading.</span></span> <span data-ttu-id="098a4-112">Zanim zostanie dodany do projektu, pojawi się okno dialogowe akceptacja licencji.</span><span class="sxs-lookup"><span data-stu-id="098a4-112">Before it is added to your project, the License Acceptance dialog will appear.</span></span> <span data-ttu-id="098a4-113">Jeśli akceptujesz postanowienia licencyjne, kliknij przycisk **akceptuję**.</span><span class="sxs-lookup"><span data-stu-id="098a4-113">If you agree to the license terms, click **I Accept**.</span></span>

5. <span data-ttu-id="098a4-114">Najnowsze zestawy programu obsługi tokenów Web JSON zostaną pobrane i dodane do projektu.</span><span class="sxs-lookup"><span data-stu-id="098a4-114">The latest JSON Web Token Handler assemblies will be downloaded and added to your project.</span></span>

## <a name="use-the-package-manager-console"></a><span data-ttu-id="098a4-115">Za pomocą konsoli Menedżera pakietów</span><span class="sxs-lookup"><span data-stu-id="098a4-115">Use the Package Manager Console</span></span>

1. <span data-ttu-id="098a4-116">W programie Visual Studio, kliknij przycisk **narzędzia** > **Menedżera pakietów NuGet** > **Konsola Menedżera pakietów**.</span><span class="sxs-lookup"><span data-stu-id="098a4-116">In Visual Studio, click **Tools** > **NuGet Package Manager** > **Package Manager Console**.</span></span>

2. <span data-ttu-id="098a4-117">**Konsola Menedżera pakietów** pojawia się.</span><span class="sxs-lookup"><span data-stu-id="098a4-117">The **Package Manager Console** appears.</span></span> <span data-ttu-id="098a4-118">Wprowadź poniższy tekst i naciśnij klawisz **Enter**:</span><span class="sxs-lookup"><span data-stu-id="098a4-118">Enter the following text and press **Enter**:</span></span>

    ```powershell
    Install-Package System.IdentityModel.Tokens.Jwt
    ```

3. <span data-ttu-id="098a4-119">Najnowsze zestawy programu obsługi tokenów Web JSON zostaną pobrane i dodane do projektu.</span><span class="sxs-lookup"><span data-stu-id="098a4-119">The latest JSON Web Token Handler assemblies will be downloaded and added to your project.</span></span>
