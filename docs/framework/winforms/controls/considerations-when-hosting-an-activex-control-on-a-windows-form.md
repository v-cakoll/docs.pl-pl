---
title: "Uwagi odnośnie do hostowania kontrolki ActiveX na formularzu systemu Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms controls, ActiveX controls
- ActiveX controls [Windows Forms], hosting
- Windows Forms, ActiveX controls
- Windows Forms, hosting ActiveX controls
- ActiveX controls [Windows Forms], adding
ms.assetid: 2509302d-a74e-484f-9890-2acdbfa67a68
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3ec828ca0b2bd8231d0baca72bf97bef566f2651
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="considerations-when-hosting-an-activex-control-on-a-windows-form"></a><span data-ttu-id="5a951-102">Uwagi odnośnie do hostowania kontrolki ActiveX na formularzu systemu Windows</span><span class="sxs-lookup"><span data-stu-id="5a951-102">Considerations When Hosting an ActiveX Control on a Windows Form</span></span>
<span data-ttu-id="5a951-103">Mimo że program Windows Forms zostały zoptymalizowane do hosta formanty formularzy systemu Windows, można nadal używać formantów ActiveX.</span><span class="sxs-lookup"><span data-stu-id="5a951-103">Although Windows Forms have been optimized to host Windows Forms controls, you can still use ActiveX controls.</span></span> <span data-ttu-id="5a951-104">Podczas planowania aplikacji korzystającej z kontrolki ActiveX, należy pamiętać o następujących kwestiach:</span><span class="sxs-lookup"><span data-stu-id="5a951-104">Keep the following considerations in mind when planning an application that uses ActiveX controls:</span></span>  
  
-   <span data-ttu-id="5a951-105">**Zabezpieczenia** środowisko uruchomieniowe języka wspólnego została rozszerzona w odniesieniu do zabezpieczenia dostępu kodu.</span><span class="sxs-lookup"><span data-stu-id="5a951-105">**Security** The common language runtime has been enhanced with regard to code access security.</span></span> <span data-ttu-id="5a951-106">Aplikacje z formularzy systemu Windows można uruchomić w pełni zaufanym środowisku bez problemu i częściowo zaufanym środowisku z większością funkcji dostępny.</span><span class="sxs-lookup"><span data-stu-id="5a951-106">Applications featuring Windows Forms can run in a fully trusted environment without issue and in a semi-trusted environment with most of the functionality accessible.</span></span> <span data-ttu-id="5a951-107">Formanty formularzy systemu Windows mogą być hostowane w przeglądarce za pomocą nie komplikacje.</span><span class="sxs-lookup"><span data-stu-id="5a951-107">Windows Forms controls can be hosted in a browser with no complications.</span></span> <span data-ttu-id="5a951-108">Formantów na formularzach systemu Windows nie można jednak korzystać z tych ulepszeń zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="5a951-108">However, ActiveX controls on Windows Forms cannot take advantage of these security enhancements.</span></span> <span data-ttu-id="5a951-109">Uruchomienie formantu ActiveX wymaga uprawnienie kodu niezarządzanego, które ustawiono <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="5a951-109">Running an ActiveX control requires unmanaged code permission, which is set with the <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="5a951-110">Aby uzyskać więcej informacji dotyczących zabezpieczeń i uprawnień kodu niezarządzanego, zobacz <xref:System.Security.Permissions.SecurityPermissionAttribute>.</span><span class="sxs-lookup"><span data-stu-id="5a951-110">For more information about security and unmanaged code permission, see <xref:System.Security.Permissions.SecurityPermissionAttribute>.</span></span>  
  
-   <span data-ttu-id="5a951-111">**Całkowity koszt użytkowania** formantów ActiveX dodany do formularza systemu Windows zostały wdrożone za pomocą formularza systemu Windows w całości, można znacznie zwiększają rozmiar plików utworzony.</span><span class="sxs-lookup"><span data-stu-id="5a951-111">**Total Cost of Ownership** ActiveX controls added to a Windows Form are deployed with that Windows Form in their entirety, which can add significantly to the size of the file(s) created.</span></span> <span data-ttu-id="5a951-112">Ponadto za pomocą formantów na formularzach systemu Windows wymaga zapisu do rejestru.</span><span class="sxs-lookup"><span data-stu-id="5a951-112">Additionally, using ActiveX controls on Windows Forms requires writing to the registry.</span></span> <span data-ttu-id="5a951-113">Jest to bardziej inwazyjne na komputerze użytkownika niż formanty formularzy systemu Windows, które nie wymagają to.</span><span class="sxs-lookup"><span data-stu-id="5a951-113">This is more invasive to a user's computer than Windows Forms controls, which do not require this.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5a951-114">Praca z ActiveX formantu wymaga użycia otoka COM interop.</span><span class="sxs-lookup"><span data-stu-id="5a951-114">Working with an ActiveX control requires the use of a COM interop wrapper.</span></span> <span data-ttu-id="5a951-115">Aby uzyskać więcej informacji, zobacz [współdziałanie COM w języku Visual Basic i Visual C#](~/docs/visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span><span class="sxs-lookup"><span data-stu-id="5a951-115">For more information, see [COM Interoperability in Visual Basic and Visual C#](~/docs/visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5a951-116">Jeśli nazwa elementu członkowskiego formantu ActiveX zgodna nazwą zdefiniowaną w [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], następnie Importer kontrolki ActiveX będzie przed nazwą elementu członkowskiego **Ctl** po tworzy <xref:System.Windows.Forms.AxHost> pochodnej klasy.</span><span class="sxs-lookup"><span data-stu-id="5a951-116">If the name of a member of the ActiveX control matches a name defined in the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], then the ActiveX Control Importer will prefix the member name with **Ctl** when it creates the <xref:System.Windows.Forms.AxHost> derived class.</span></span> <span data-ttu-id="5a951-117">Na przykład, jeśli formant ActiveX ma element członkowski o nazwie **układu**, jego nazwa zostanie zmieniona **CtlLayout** w klasie pochodnej AxHost ponieważ **układu** zdarzeń jest zdefiniowana w [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5a951-117">For example, if your ActiveX control has a member named **Layout**, it is renamed **CtlLayout** in the AxHost-derived class because the **Layout** event is defined within the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a951-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5a951-118">See Also</span></span>  
 [<span data-ttu-id="5a951-119">Porady: dodawanie formantów ActiveX do formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="5a951-119">How to: Add ActiveX Controls to Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-add-activex-controls-to-windows-forms.md)  
 [<span data-ttu-id="5a951-120">Zabezpieczenia dostępu kodu</span><span class="sxs-lookup"><span data-stu-id="5a951-120">Code Access Security</span></span>](../../../../docs/framework/misc/code-access-security.md)  
 [<span data-ttu-id="5a951-121">Formanty i obiektów programowalnych w różnych językach i biblioteki</span><span class="sxs-lookup"><span data-stu-id="5a951-121">Controls and Programmable Objects Compared in Various Languages and Libraries</span></span>](http://msdn.microsoft.com/en-us/021f2a1b-8247-4348-a5ad-e1d9ab23004b)  
 [<span data-ttu-id="5a951-122">Umieszczanie formantów na formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="5a951-122">Putting Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/putting-controls-on-windows-forms.md)  
 [<span data-ttu-id="5a951-123">Formanty formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="5a951-123">Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/index.md)
