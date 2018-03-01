---
title: "Wdrażanie aplikacji, które odwołują się do formantów Powerpack (Visual Studio)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Power Packs, deploying
ms.assetid: f2230f53-a745-4731-89e6-033943faa209
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2a9562acf05cd27eed7bc1ad963845af9a7ca5f9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="deploying-applications-that-reference-power-packs-controls-visual-studio"></a><span data-ttu-id="e898c-102">Wdrażanie aplikacji, które odwołują się do formantów Powerpack (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="e898c-102">Deploying applications that reference Power Packs controls (Visual Studio)</span></span>
<span data-ttu-id="e898c-103">Jeśli chcesz wdrożyć aplikację, która odwołuje się do formantów Powerpack (<xref:Microsoft.VisualBasic.PowerPacks.LineShape>, <xref:Microsoft.VisualBasic.PowerPacks.OvalShape>, <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape>, lub <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>), kontrolki musi być zainstalowany na komputerze docelowym.</span><span class="sxs-lookup"><span data-stu-id="e898c-103">If you want to deploy an application that references the Power Packs controls (<xref:Microsoft.VisualBasic.PowerPacks.LineShape>, <xref:Microsoft.VisualBasic.PowerPacks.OvalShape>, <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape>, or <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>), the controls must be installed on the destination computer.</span></span>  
  
## <a name="installing-the-power-packs-controls-as-a-prerequisite"></a><span data-ttu-id="e898c-104">Instalowanie formantów Powerpack jako warunek wstępny</span><span class="sxs-lookup"><span data-stu-id="e898c-104">Installing the Power Packs controls as a prerequisite</span></span>  
 <span data-ttu-id="e898c-105">Aby pomyślnie wdrożyć aplikację, należy wdrożyć wszystkie składniki, które są używane przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="e898c-105">To successfully deploy an application, you must also deploy all components that are referenced by the application.</span></span> <span data-ttu-id="e898c-106">Proces instalowania składników wymaganych wstępnie nosi nazwę *uruchamianie*.</span><span class="sxs-lookup"><span data-stu-id="e898c-106">The process of installing prerequisite components is known as *bootstrapping*.</span></span>  
  
 <span data-ttu-id="e898c-107">Gdy [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] jest zainstalowany na komputerze deweloperskim Powerpack, pakiet programu inicjującego jest dodawany do [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] katalogu programu inicjującego.</span><span class="sxs-lookup"><span data-stu-id="e898c-107">When [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] is installed on your development computer, a Power Packs bootstrapper package is added to the [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] bootstrapper directory.</span></span> <span data-ttu-id="e898c-108">Ten pakiet jest dostępna po wykonaniu procedury dodawania wymagania wstępne dotyczące albo [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] lub wdrożenia Instalatora Windows.</span><span class="sxs-lookup"><span data-stu-id="e898c-108">This package is then available when you follow the procedures for adding prerequisites for either [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] or Windows Installer deployment.</span></span>  
  
 <span data-ttu-id="e898c-109">Domyślnie zainicjowano składniki są wdrażane z tej samej lokalizacji co pakiet instalacyjny.</span><span class="sxs-lookup"><span data-stu-id="e898c-109">By default, bootstrapped components are deployed from the same location as the installation package.</span></span> <span data-ttu-id="e898c-110">Alternatywnie można wdrożyć składniki z adresu URL lub pliku lokalizację udziału, w którym użytkownicy mogą pobrać je w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="e898c-110">Alternatively, you can choose to deploy the components from a URL or file share location from which users can download them as necessary.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e898c-111">Aby zainstalować składniki zainicjowano, użytkownik może być konieczne uprawnienia użytkownika administracyjnego lub podobne na komputerze.</span><span class="sxs-lookup"><span data-stu-id="e898c-111">To install bootstrapped components, the user might need administrative or similar user permissions on the computer.</span></span> <span data-ttu-id="e898c-112">Dla [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] aplikacji, oznacza to, że użytkownik będzie musiał uprawnień administracyjnych do zainstalowania aplikacji, niezależnie od poziomu zabezpieczeń, określonym przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="e898c-112">For [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] applications, this means that the user will need administrative permissions to install the application, regardless of the security level specified by the application.</span></span> <span data-ttu-id="e898c-113">Po zainstalowaniu aplikacji, użytkownik będzie mógł uruchomić aplikację bez uprawnień administracyjnych.</span><span class="sxs-lookup"><span data-stu-id="e898c-113">After the application is installed, the user can run the application without administrative permissions.</span></span>  
  
 <span data-ttu-id="e898c-114">Podczas instalacji użytkownicy otrzymują monit do zainstalowania formantów Powerpack, jeśli nie są dostępne na komputerze docelowym.</span><span class="sxs-lookup"><span data-stu-id="e898c-114">During installation, users will be prompted to install the Power Packs controls if they are not present on the destination computer.</span></span>  
  
 <span data-ttu-id="e898c-115">Alternatywą wobec uruchamianie wstępnie wdrożeniem formantów Powerpack przy użyciu systemu dystrybucji oprogramowania elektronicznych, takich jak Microsoft Systems Management Server.</span><span class="sxs-lookup"><span data-stu-id="e898c-115">As an alternative to bootstrapping, you can pre-deploy the Power Packs controls by using an electronic software distribution system such as Microsoft Systems Management Server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e898c-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e898c-116">See also</span></span>  
 [<span data-ttu-id="e898c-117">Porady: Instalowanie wymagań wstępnych za pomocą aplikacji ClickOnce</span><span class="sxs-lookup"><span data-stu-id="e898c-117">How to: Install Prerequisites with a ClickOnce Application</span></span>](/visualstudio/deployment/how-to-install-prerequisites-with-a-clickonce-application)  
 [<span data-ttu-id="e898c-118">Formantów Powerpack Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e898c-118">Visual Basic Power Packs Controls</span></span>](../../../visual-basic/developing-apps/windows-forms/power-packs-controls.md)
