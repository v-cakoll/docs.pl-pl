---
title: "Pobieranie pakietu sprawdzania poprawności rejestru nazwy dostawcy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ff8b0014-c5d4-4614-90f0-13fcc0ba777a
caps.latest.revision: "3"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9bf6869de939ed7eda7cd3de868e712126f71751
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="downloading-the-validating-issuer-name-registry-package"></a><span data-ttu-id="22017-102">Pobieranie pakietu sprawdzania poprawności rejestru nazwy dostawcy</span><span class="sxs-lookup"><span data-stu-id="22017-102">Downloading the Validating Issuer Name Registry Package</span></span>
<span data-ttu-id="22017-103">W tym temacie omówiono sposób pobranie i użycie rejestru nazwy wystawcy sprawdzania poprawności (VINR) w projekcie.</span><span class="sxs-lookup"><span data-stu-id="22017-103">This topic discusses how to download and use the Validating Issuer Name Registry (VINR) in your project.</span></span>  
  
## <a name="downloading-the-validating-issuer-name-registry"></a><span data-ttu-id="22017-104">Pobieranie sprawdzania poprawności rejestru nazwy dostawcy</span><span class="sxs-lookup"><span data-stu-id="22017-104">Downloading the Validating Issuer Name Registry</span></span>  
 <span data-ttu-id="22017-105">VINR jest dostępna jako pakietu NuGet, który dodaje konieczne zestawy, a odwołania do projektu.</span><span class="sxs-lookup"><span data-stu-id="22017-105">The VINR is available as a NuGet package, which adds the necessary assemblies and references to your project.</span></span> <span data-ttu-id="22017-106">Jeśli nie masz już zainstalowany NuGet, przejdź do [nuget.org](http://nuget.org) go zainstalować.</span><span class="sxs-lookup"><span data-stu-id="22017-106">If you do not already have NuGet installed, go to [nuget.org](http://nuget.org) to install it.</span></span> <span data-ttu-id="22017-107">Widać Historia wersji rozszerzenia odwiedzając jej stronę na NuGet: [rejestru sprawdzania poprawności nazwy wystawcy firmy Microsoft na NuGet](https://nuget.org/packages/System.IdentityModel.Tokens.ValidatingIssuerNameRegistry/)</span><span class="sxs-lookup"><span data-stu-id="22017-107">You can see the versioning history for the extension by visiting its page on NuGet: [Microsoft Validating Issuer Name Registry on NuGet](https://nuget.org/packages/System.IdentityModel.Tokens.ValidatingIssuerNameRegistry/)</span></span>  
  
#### <a name="downloading-the-validating-issuer-name-registry-by-using-the-package-manager-gui"></a><span data-ttu-id="22017-108">Pobieranie sprawdzanie poprawności rejestru nazwy dostawcy przy użyciu graficznego interfejsu użytkownika Menedżera pakietów</span><span class="sxs-lookup"><span data-stu-id="22017-108">Downloading the Validating Issuer Name Registry by using the Package Manager GUI</span></span>  
  
1.  <span data-ttu-id="22017-109">W programie Visual Studio, kliknij prawym przyciskiem myszy projekt w **Eksploratora rozwiązań**, a następnie wybierz **Zarządzaj pakietami NuGet**.</span><span class="sxs-lookup"><span data-stu-id="22017-109">In Visual Studio, right-click your project in **Solution Explorer**, and then select **Manage NuGet Packages**.</span></span>  
  
2.  <span data-ttu-id="22017-110">W **Zarządzaj pakietami NuGet** okna, kliknij pole wyszukiwania i wprowadź `ValidatingIssuerNameRegistry` i naciśnij klawisz **Enter**.</span><span class="sxs-lookup"><span data-stu-id="22017-110">In the **Manage NuGet Packages** window, click the search box and enter `ValidatingIssuerNameRegistry` and press **Enter**.</span></span>  
  
3.  <span data-ttu-id="22017-111">W okienku wyników kliknij **zainstalować** przycisku do pierwszego wyniku.</span><span class="sxs-lookup"><span data-stu-id="22017-111">From the results pane, click the **Install** button for the first result.</span></span>  
  
4.  <span data-ttu-id="22017-112">Pakiet zostanie rozpocząć pobieranie.</span><span class="sxs-lookup"><span data-stu-id="22017-112">The package will begin downloading.</span></span> <span data-ttu-id="22017-113">Przed dodaniem jej do projektu, pojawi się okno dialogowe akceptacji licencji.</span><span class="sxs-lookup"><span data-stu-id="22017-113">Before it is added to your project, the License Acceptance dialog will appear.</span></span> <span data-ttu-id="22017-114">Jeśli akceptujesz postanowienia licencyjne, kliknij przycisk **akceptuję**.</span><span class="sxs-lookup"><span data-stu-id="22017-114">If you agree to the license terms, click **I Accept**.</span></span>  
  
5.  <span data-ttu-id="22017-115">Najnowsze zestawy VINR zostanie pobrany i dodane do projektu.</span><span class="sxs-lookup"><span data-stu-id="22017-115">The latest VINR assemblies will be downloaded and added to your project.</span></span>  
  
#### <a name="downloading-the-validating-issuer-name-registry-by-using-the-package-manager-console"></a><span data-ttu-id="22017-116">Pobieranie sprawdzanie poprawności rejestru nazwy dostawcy przy użyciu konsoli Menedżera pakietów</span><span class="sxs-lookup"><span data-stu-id="22017-116">Downloading the Validating Issuer Name Registry by using the Package Manager Console</span></span>  
  
1.  <span data-ttu-id="22017-117">W programie Visual Studio, kliknij przycisk **narzędzia**, **Menedżer pakietów biblioteki**, a następnie **Konsola Menedżera pakietów**.</span><span class="sxs-lookup"><span data-stu-id="22017-117">In Visual Studio, click **Tools**, **Library Package Manager**, and then **Package Manager Console**.</span></span>  
  
2.  <span data-ttu-id="22017-118">**Konsola Menedżera pakietów** pojawi się.</span><span class="sxs-lookup"><span data-stu-id="22017-118">The **Package Manager Console** appears.</span></span> <span data-ttu-id="22017-119">Wprowadź poniższy tekst i naciśnij klawisz **Enter**:</span><span class="sxs-lookup"><span data-stu-id="22017-119">Enter the following text and press **Enter**:</span></span>  
  
    ```powershell  
    Install-Package System.IdentityModel.Tokens.ValidatingIssuerNameRegistry  
    ```  
  
3.  <span data-ttu-id="22017-120">Najnowsze zestawy VINR zostanie pobrany i dodane do projektu.</span><span class="sxs-lookup"><span data-stu-id="22017-120">The latest VINR assemblies will be downloaded and added to your project.</span></span>
