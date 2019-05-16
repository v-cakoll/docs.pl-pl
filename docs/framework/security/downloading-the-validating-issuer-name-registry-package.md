---
title: Pobieranie pakietu sprawdzania poprawności rejestru nazwy dostawcy
ms.date: 10/10/2018
ms.assetid: ff8b0014-c5d4-4614-90f0-13fcc0ba777a
ms.openlocfilehash: 5684844f1db33b075df099b3026d9d0c1061199f
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65631844"
---
# <a name="download-the-validating-issuer-name-registry-package"></a><span data-ttu-id="31c2b-102">Pobieranie pakietu sprawdzania poprawności rejestru nazwy wystawcy</span><span class="sxs-lookup"><span data-stu-id="31c2b-102">Download the Validating Issuer Name Registry Package</span></span>

<span data-ttu-id="31c2b-103">W tym temacie omówiono sposób pobierania i wykorzystywania rejestru nazwy wystawcy sprawdzania poprawności (VINR) w projekcie.</span><span class="sxs-lookup"><span data-stu-id="31c2b-103">This topic discusses how to download and use the Validating Issuer Name Registry (VINR) in your project.</span></span>

<span data-ttu-id="31c2b-104">Rozszerzenie VINR jest dostępne jako pakiet NuGet, który dodaje niezbędne zespoły i odwołania do projektu.</span><span class="sxs-lookup"><span data-stu-id="31c2b-104">The VINR is available as a NuGet package, which adds the necessary assemblies and references to your project.</span></span> <span data-ttu-id="31c2b-105">Jeśli nie masz jeszcze zainstalowanego Menedżera NuGet, przejdź do strony [nuget.org](https://nuget.org) go zainstalować.</span><span class="sxs-lookup"><span data-stu-id="31c2b-105">If you do not already have NuGet installed, go to [nuget.org](https://nuget.org) to install it.</span></span> <span data-ttu-id="31c2b-106">Można wyświetlić historię wersji rozszerzenia odwiedzając jego stronę na NuGet: [Microsoft, sprawdzanie poprawności rejestru nazwy wystawcy dla narzędzia NuGet](https://nuget.org/packages/System.IdentityModel.Tokens.ValidatingIssuerNameRegistry/)</span><span class="sxs-lookup"><span data-stu-id="31c2b-106">You can see the versioning history for the extension by visiting its page on NuGet: [Microsoft Validating Issuer Name Registry on NuGet](https://nuget.org/packages/System.IdentityModel.Tokens.ValidatingIssuerNameRegistry/)</span></span>

## <a name="use-the-package-manager-gui"></a><span data-ttu-id="31c2b-107">Użyj Menedżera pakietów GUI</span><span class="sxs-lookup"><span data-stu-id="31c2b-107">Use the Package Manager GUI</span></span>

1. <span data-ttu-id="31c2b-108">W programie Visual Studio, kliknij prawym przyciskiem myszy projekt w **Eksploratora rozwiązań**, a następnie wybierz pozycję **Zarządzaj pakietami NuGet**.</span><span class="sxs-lookup"><span data-stu-id="31c2b-108">In Visual Studio, right-click your project in **Solution Explorer**, and then select **Manage NuGet Packages**.</span></span>

2. <span data-ttu-id="31c2b-109">W **Zarządzaj pakietami NuGet** okna, kliknij pole wyszukiwania i wprowadź `ValidatingIssuerNameRegistry` i naciśnij klawisz **Enter**.</span><span class="sxs-lookup"><span data-stu-id="31c2b-109">In the **Manage NuGet Packages** window, click the search box and enter `ValidatingIssuerNameRegistry` and press **Enter**.</span></span>

3. <span data-ttu-id="31c2b-110">W okienku wyników kliknij **zainstalować** przycisku dla pierwszego wyniku.</span><span class="sxs-lookup"><span data-stu-id="31c2b-110">From the results pane, click the **Install** button for the first result.</span></span>

4. <span data-ttu-id="31c2b-111">Pakiet rozpocznie się pobieranie.</span><span class="sxs-lookup"><span data-stu-id="31c2b-111">The package will begin downloading.</span></span> <span data-ttu-id="31c2b-112">Zanim zostanie dodany do projektu, pojawi się okno dialogowe akceptacja licencji.</span><span class="sxs-lookup"><span data-stu-id="31c2b-112">Before it is added to your project, the License Acceptance dialog will appear.</span></span> <span data-ttu-id="31c2b-113">Jeśli akceptujesz postanowienia licencyjne, kliknij przycisk **akceptuję**.</span><span class="sxs-lookup"><span data-stu-id="31c2b-113">If you agree to the license terms, click **I Accept**.</span></span>

5. <span data-ttu-id="31c2b-114">Najnowsze zestawy VINR zostaną pobrane i dodane do projektu.</span><span class="sxs-lookup"><span data-stu-id="31c2b-114">The latest VINR assemblies will be downloaded and added to your project.</span></span>

## <a name="use-the-package-manager-console"></a><span data-ttu-id="31c2b-115">Za pomocą konsoli Menedżera pakietów</span><span class="sxs-lookup"><span data-stu-id="31c2b-115">Use the Package Manager Console</span></span>

1. <span data-ttu-id="31c2b-116">W programie Visual Studio, kliknij przycisk **narzędzia** > **Menedżera pakietów NuGet** > **Konsola Menedżera pakietów**.</span><span class="sxs-lookup"><span data-stu-id="31c2b-116">In Visual Studio, click **Tools** > **NuGet Package Manager** > **Package Manager Console**.</span></span>

2. <span data-ttu-id="31c2b-117">**Konsola Menedżera pakietów** pojawia się.</span><span class="sxs-lookup"><span data-stu-id="31c2b-117">The **Package Manager Console** appears.</span></span> <span data-ttu-id="31c2b-118">Wprowadź poniższy tekst i naciśnij klawisz **Enter**:</span><span class="sxs-lookup"><span data-stu-id="31c2b-118">Enter the following text and press **Enter**:</span></span>

    ```powershell
    Install-Package System.IdentityModel.Tokens.ValidatingIssuerNameRegistry
    ```

3. <span data-ttu-id="31c2b-119">Najnowsze zestawy VINR zostaną pobrane i dodane do projektu.</span><span class="sxs-lookup"><span data-stu-id="31c2b-119">The latest VINR assemblies will be downloaded and added to your project.</span></span>
