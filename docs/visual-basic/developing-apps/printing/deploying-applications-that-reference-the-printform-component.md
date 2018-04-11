---
title: Wdrażanie aplikacji, które odwołują się do wyniku składnik PrintForm (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- PrintForm component [Visual Basic], deploying
ms.assetid: b595ea44-a712-4625-a761-190c64f59bbe
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 15b6e21e769c90e23e66e4f87b37f74462423985
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/10/2018
---
# <a name="deploying-applications-that-reference-the-printform-component-visual-basic"></a><span data-ttu-id="85803-102">Wdrażanie aplikacji, które odwołują się do wyniku składnik PrintForm (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="85803-102">Deploying applications that reference the PrintForm component (Visual Basic)</span></span>
<span data-ttu-id="85803-103">Jeśli chcesz wdrożyć aplikację, która odwołuje się do <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> składnika, składnik musi być zainstalowany na komputerze docelowym.</span><span class="sxs-lookup"><span data-stu-id="85803-103">If you want to deploy an application that references the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component, the component must be installed on the destination computer.</span></span>  
  
 <span data-ttu-id="85803-104">Formantów PowerPack nie są uwzględnione w programie Visual Studio, ale można pobrać je z [Centrum pobierania](http://www.microsoft.com/en-us/download/details.aspx?id=25169).</span><span class="sxs-lookup"><span data-stu-id="85803-104">The PowerPack controls are no longer included in Visual Studio, but you can download them from the [Download Center](http://www.microsoft.com/en-us/download/details.aspx?id=25169).</span></span>  
  
## <a name="installing-the-printform-as-a-prerequisite"></a><span data-ttu-id="85803-105">Instalowanie PrintForm jako warunek wstępny</span><span class="sxs-lookup"><span data-stu-id="85803-105">Installing the PrintForm as a prerequisite</span></span>  
 <span data-ttu-id="85803-106">Aby pomyślnie wdrożyć aplikację, należy wdrożyć wszystkie składniki, które są używane przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="85803-106">To successfully deploy an application, you must also deploy all components that are referenced by the application.</span></span> <span data-ttu-id="85803-107">Proces instalowania składników wymaganych wstępnie nosi nazwę *uruchamianie*.</span><span class="sxs-lookup"><span data-stu-id="85803-107">The process of installing prerequisite components is known as *bootstrapping*.</span></span>  
  
 <span data-ttu-id="85803-108">Gdy <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> składnik jest zainstalowany na komputerze deweloperskim, pakiet programu inicjującego Microsoft Visual Basic Powerpack jest dodawany do [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] katalogu programu inicjującego.</span><span class="sxs-lookup"><span data-stu-id="85803-108">When the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component is installed on your development computer, a Microsoft Visual Basic Power Packs bootstrapper package is added to the [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] bootstrapper directory.</span></span> <span data-ttu-id="85803-109">Ten pakiet jest dostępna po wykonaniu procedury dodawania wymagania wstępne dotyczące albo [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] lub wdrożenia Instalatora Windows.</span><span class="sxs-lookup"><span data-stu-id="85803-109">This package is then available when you follow the procedures for adding prerequisites for either [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] or Windows Installer deployment.</span></span>  
  
 <span data-ttu-id="85803-110">Domyślnie zainicjowano składniki są wdrażane z tej samej lokalizacji co pakiet instalacyjny.</span><span class="sxs-lookup"><span data-stu-id="85803-110">By default, bootstrapped components are deployed from the same location as the installation package.</span></span> <span data-ttu-id="85803-111">Alternatywnie można wdrożyć składniki z adresu URL lub pliku lokalizację udziału, w którym użytkownicy mogą pobrać je w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="85803-111">Alternatively, you can choose to deploy the components from a URL or file share location from which users can download them as necessary.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="85803-112">Aby zainstalować składniki zainicjowano, użytkownik może być konieczne uprawnienia użytkownika administracyjnego lub podobne na komputerze.</span><span class="sxs-lookup"><span data-stu-id="85803-112">To install bootstrapped components, the user might need administrative or similar user permissions on the computer.</span></span> <span data-ttu-id="85803-113">Dla [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] aplikacji, oznacza to, że użytkownik będzie musiał uprawnień administracyjnych do zainstalowania aplikacji, niezależnie od poziomu zabezpieczeń, określonym przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="85803-113">For [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] applications, this means that the user will need administrative permissions to install the application, regardless of the security level specified by the application.</span></span> <span data-ttu-id="85803-114">Po zainstalowaniu aplikacji, użytkownik będzie mógł uruchomić aplikację bez uprawnień administracyjnych.</span><span class="sxs-lookup"><span data-stu-id="85803-114">After the application is installed, the user can run the application without administrative permissions.</span></span>  
  
 <span data-ttu-id="85803-115">Podczas instalacji, użytkownicy będą monitowani do zainstalowania <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> składników, jeśli nie ma go na komputerze docelowym.</span><span class="sxs-lookup"><span data-stu-id="85803-115">During installation, users will be prompted to install the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component if it is not present on the destination computer.</span></span>  
  
 <span data-ttu-id="85803-116">Alternatywą dla uruchamianie przed wdrożeniem <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> składnika przy użyciu systemu dystrybucji oprogramowania elektronicznych, takich jak Microsoft Systems Management Server.</span><span class="sxs-lookup"><span data-stu-id="85803-116">As an alternative to bootstrapping, you can pre-deploy the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component by using an electronic software distribution system like Microsoft Systems Management Server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85803-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="85803-117">See also</span></span>  
 [<span data-ttu-id="85803-118">Instrukcje: instalowanie wstępnie wymaganych składników za pomocą aplikacji ClickOnce</span><span class="sxs-lookup"><span data-stu-id="85803-118">How to: Install Prerequisites with a ClickOnce Application</span></span>](/visualstudio/deployment/how-to-install-prerequisites-with-a-clickonce-application)  
 [<span data-ttu-id="85803-119">Składnik PrintForm</span><span class="sxs-lookup"><span data-stu-id="85803-119">PrintForm Component</span></span>](../../../visual-basic/developing-apps/printing/printform-component.md)
