---
title: "Konfigurowanie własnej aplikacji"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a2f995b0-669d-4721-b00f-4561ec7eb6a4
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 72fd6dba860906fb87d67e19148f13b70dc64136
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="configuring-your-application"></a><span data-ttu-id="a47fb-102">Konfigurowanie własnej aplikacji</span><span class="sxs-lookup"><span data-stu-id="a47fb-102">Configuring Your Application</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="a47fb-103">używa systemu konfiguracji platformy .NET i pozwala na skonfigurowanie usługi w zakresie komputera i aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a47fb-103"> uses the .NET configuration system and allows you to configure services at both the machine and application scope.</span></span>  
  
 <span data-ttu-id="a47fb-104">Konfiguracja ustawień zdefiniowanych przez [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] znajdują się w `<system.serviceModel>` grupy sekcji.</span><span class="sxs-lookup"><span data-stu-id="a47fb-104">Configuration settings defined by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] are located in the `<system.serviceModel>` section group.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="a47fb-105">jak skonfigurować [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi, zobacz następujące tematy:</span><span class="sxs-lookup"><span data-stu-id="a47fb-105"> how to configure a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service, see the following topics:</span></span>  
  
-   [<span data-ttu-id="a47fb-106">Konfigurowanie usług</span><span class="sxs-lookup"><span data-stu-id="a47fb-106">Configuring Services</span></span>](../../../../docs/framework/wcf/configuring-services.md)  
  
-   [<span data-ttu-id="a47fb-107">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="a47fb-107">\<system.serviceModel></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)  
  
 <span data-ttu-id="a47fb-108">Ustawienia zdefiniowane przez aplikację konfiguracje są definiowane w `<appSettings>` grupy sekcji.</span><span class="sxs-lookup"><span data-stu-id="a47fb-108">Application-defined configurations settings are defined in the `<appSettings>` section group.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="a47fb-109">Ustawienia aplikacji w plikach konfiguracji platformy .NET, zobacz [ \<appSettings >](http://go.microsoft.com/fwlink/?LinkId=95159).</span><span class="sxs-lookup"><span data-stu-id="a47fb-109"> application settings in .NET configuration files, see [\<appSettings>](http://go.microsoft.com/fwlink/?LinkId=95159).</span></span>  
  
## <a name="using-the-configuration-editor"></a><span data-ttu-id="a47fb-110">Za pomocą edytora konfiguracji</span><span class="sxs-lookup"><span data-stu-id="a47fb-110">Using the Configuration Editor</span></span>  
 <span data-ttu-id="a47fb-111">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] [Narzędzie edytora konfiguracji (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) umożliwia administratorów i deweloperów, tworzenie i modyfikowanie ustawień konfiguracji [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usług przy użyciu graficznego interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="a47fb-111">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)][Configuration Editor Tool (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) allows administrators and developers to create and modify configuration settings for [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services using a graphical user interface.</span></span> <span data-ttu-id="a47fb-112">Z tego narzędzia można zarządzać ustawieniami dla [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] powiązania zachowania, usług i diagnostyki bez konieczności bezpośredniego edytowania plików XML konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="a47fb-112">With this tool, you can manage settings for [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] bindings, behaviors, services, and diagnostics without directly editing XML configuration files.</span></span>  
  
## <a name="editing-configuration-files-in-visual-studio"></a><span data-ttu-id="a47fb-113">Edycję plików konfiguracyjnych w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="a47fb-113">Editing Configuration Files in Visual Studio</span></span>  
 <span data-ttu-id="a47fb-114">Na edycję pliku konfiguracyjnego z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] projekt usługi w [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)], kliknij prawym przyciskiem myszy w **Eksploratora rozwiązań** i wybierz polecenie **Edycja konfiguracji WCF** elementu menu kontekstowego.</span><span class="sxs-lookup"><span data-stu-id="a47fb-114">To edit the configuration file of a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service project in [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)], right click it in **Solution Explorer** and choose the **Edit WCF Config** context menu item.</span></span> <span data-ttu-id="a47fb-115">Spowoduje to uruchomienie [narzędzie edytora konfiguracji (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).</span><span class="sxs-lookup"><span data-stu-id="a47fb-115">This launches the [Configuration Editor Tool (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a47fb-116">Po zmodyfikowaniu pliku konfiguracyjnego [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] projekt usługi sieci Web w [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] klikając prawym przyciskiem myszy w **Eksploratora rozwiązań**, zwróć uwagę, że **Edycja konfiguracji WCF** brakuje elementu menu kontekstowego .</span><span class="sxs-lookup"><span data-stu-id="a47fb-116">If you edit the configuration file of a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Web Service project in [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] by right-clicking it in **Solution Explorer**, notice that the **Edit WCF Config** context menu item is missing.</span></span> <span data-ttu-id="a47fb-117">Obejście tego problemu, kliknij przycisk **narzędzia** menu i wybierz polecenie **Edytor konfiguracji usługi WCF**.</span><span class="sxs-lookup"><span data-stu-id="a47fb-117">To workaround this issue, click the **Tools** menu, and choose **WCF Service Config Editor**.</span></span> <span data-ttu-id="a47fb-118">Po tym, kliknij prawym przyciskiem myszy plik konfiguracji i użyj **Edycja konfiguracji WCF** elementu menu kontekstowego.</span><span class="sxs-lookup"><span data-stu-id="a47fb-118">After that, you can right-click a configuration file and use the **Edit WCF Config** context menu item.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a47fb-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a47fb-119">See Also</span></span>  
 [<span data-ttu-id="a47fb-120">Narzędzie edytora konfiguracji (SvcConfigEditor.exe)</span><span class="sxs-lookup"><span data-stu-id="a47fb-120">Configuration Editor Tool (SvcConfigEditor.exe)</span></span>](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)  
 [<span data-ttu-id="a47fb-121">Konfigurowanie usług</span><span class="sxs-lookup"><span data-stu-id="a47fb-121">Configuring Services</span></span>](../../../../docs/framework/wcf/configuring-services.md)  
 [<span data-ttu-id="a47fb-122">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="a47fb-122">\<system.serviceModel></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)
