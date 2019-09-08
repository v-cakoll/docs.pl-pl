---
title: Konfigurowanie własnej aplikacji
ms.date: 03/30/2017
ms.assetid: a2f995b0-669d-4721-b00f-4561ec7eb6a4
ms.openlocfilehash: 4e19e4d0ecb6bc90402f99dddd280ee1dbcf7ea0
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798150"
---
# <a name="configuring-your-application"></a><span data-ttu-id="9a609-102">Konfigurowanie własnej aplikacji</span><span class="sxs-lookup"><span data-stu-id="9a609-102">Configuring Your Application</span></span>
<span data-ttu-id="9a609-103">Windows Communication Foundation (WCF) korzysta z systemu konfiguracji platformy .NET i umożliwia konfigurowanie usług zarówno w zakresie komputera, jak i aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9a609-103">Windows Communication Foundation (WCF) uses the .NET configuration system and allows you to configure services at both the machine and application scope.</span></span>  
  
 <span data-ttu-id="9a609-104">Ustawienia konfiguracji zdefiniowane przez funkcję WCF znajdują się `<system.serviceModel>` w grupie sekcji.</span><span class="sxs-lookup"><span data-stu-id="9a609-104">Configuration settings defined by WCF are located in the `<system.serviceModel>` section group.</span></span> <span data-ttu-id="9a609-105">Więcej informacji o sposobie konfigurowania usługi WCF znajduje się w następujących tematach:</span><span class="sxs-lookup"><span data-stu-id="9a609-105">For more information about how to configure a WCF service, see the following topics:</span></span>  
  
- [<span data-ttu-id="9a609-106">Konfigurowanie usług</span><span class="sxs-lookup"><span data-stu-id="9a609-106">Configuring Services</span></span>](../configuring-services.md)  
  
- [<span data-ttu-id="9a609-107">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="9a609-107">\<system.serviceModel></span></span>](../../configure-apps/file-schema/wcf/system-servicemodel.md)  
  
 <span data-ttu-id="9a609-108">Ustawienia konfiguracji zdefiniowane przez aplikację są zdefiniowane w `<appSettings>` grupie sekcji.</span><span class="sxs-lookup"><span data-stu-id="9a609-108">Application-defined configurations settings are defined in the `<appSettings>` section group.</span></span> <span data-ttu-id="9a609-109">Aby uzyskać więcej informacji na temat ustawień aplikacji w plikach konfiguracji platformy .NET, zobacz [ \<AppSettings >](https://go.microsoft.com/fwlink/?LinkId=95159).</span><span class="sxs-lookup"><span data-stu-id="9a609-109">For more information about application settings in .NET configuration files, see [\<appSettings>](https://go.microsoft.com/fwlink/?LinkId=95159).</span></span>  
  
## <a name="using-the-configuration-editor"></a><span data-ttu-id="9a609-110">Korzystanie z edytora konfiguracji</span><span class="sxs-lookup"><span data-stu-id="9a609-110">Using the Configuration Editor</span></span>  
 <span data-ttu-id="9a609-111">[Narzędzie Edytor konfiguracji WCF (SvcConfigEditor. exe)](../configuration-editor-tool-svcconfigeditor-exe.md) umożliwia administratorom i deweloperom tworzenie i modyfikowanie ustawień konfiguracji usług WCF przy użyciu graficznego interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="9a609-111">The WCF [Configuration Editor Tool (SvcConfigEditor.exe)](../configuration-editor-tool-svcconfigeditor-exe.md) allows administrators and developers to create and modify configuration settings for WCF services using a graphical user interface.</span></span> <span data-ttu-id="9a609-112">Za pomocą tego narzędzia można zarządzać ustawieniami powiązań programu WCF, zachowań, usług i diagnostyki bez bezpośredniego edytowania plików konfiguracji XML.</span><span class="sxs-lookup"><span data-stu-id="9a609-112">With this tool, you can manage settings for WCF bindings, behaviors, services, and diagnostics without directly editing XML configuration files.</span></span>  
  
## <a name="editing-configuration-files-in-visual-studio"></a><span data-ttu-id="9a609-113">Edytowanie plików konfiguracji w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="9a609-113">Editing Configuration Files in Visual Studio</span></span>  
 <span data-ttu-id="9a609-114">Aby edytować plik konfiguracji projektu usługi WCF w programie Visual Studio, kliknij prawym przyciskiem myszy w **Eksplorator rozwiązań** i wybierz pozycję **Edytuj kontekst konfiguracji WCF** .</span><span class="sxs-lookup"><span data-stu-id="9a609-114">To edit the configuration file of a WCF service project in Visual Studio, right click it in **Solution Explorer** and choose the **Edit WCF Config** context menu item.</span></span> <span data-ttu-id="9a609-115">Spowoduje to uruchomienie [Narzędzia Edytora konfiguracji (SvcConfigEditor. exe)](../configuration-editor-tool-svcconfigeditor-exe.md).</span><span class="sxs-lookup"><span data-stu-id="9a609-115">This launches the [Configuration Editor Tool (SvcConfigEditor.exe)](../configuration-editor-tool-svcconfigeditor-exe.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9a609-116">Jeśli edytujesz plik konfiguracyjny projektu usługi sieci Web WCF w programie Visual Studio, klikając go prawym przyciskiem myszy w **Eksplorator rozwiązań**, Zauważ, że brakuje elementu menu kontekstowego **konfiguracji WCF** .</span><span class="sxs-lookup"><span data-stu-id="9a609-116">If you edit the configuration file of a WCF Web Service project in Visual Studio by right-clicking it in **Solution Explorer**, notice that the **Edit WCF Config** context menu item is missing.</span></span> <span data-ttu-id="9a609-117">Aby obejść ten problem, kliknij menu **Narzędzia** , a następnie wybierz pozycję **Edytor konfiguracji usługi WCF**.</span><span class="sxs-lookup"><span data-stu-id="9a609-117">To workaround this issue, click the **Tools** menu, and choose **WCF Service Config Editor**.</span></span> <span data-ttu-id="9a609-118">Następnie możesz kliknąć prawym przyciskiem myszy plik konfiguracyjny i użyć elementu menu kontekstowego **edytowania konfiguracji WCF** .</span><span class="sxs-lookup"><span data-stu-id="9a609-118">After that, you can right-click a configuration file and use the **Edit WCF Config** context menu item.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a609-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9a609-119">See also</span></span>

- [<span data-ttu-id="9a609-120">Narzędzie edytora konfiguracji (SvcConfigEditor.exe)</span><span class="sxs-lookup"><span data-stu-id="9a609-120">Configuration Editor Tool (SvcConfigEditor.exe)</span></span>](../configuration-editor-tool-svcconfigeditor-exe.md)
- [<span data-ttu-id="9a609-121">Konfigurowanie usług</span><span class="sxs-lookup"><span data-stu-id="9a609-121">Configuring Services</span></span>](../configuring-services.md)
- [<span data-ttu-id="9a609-122">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="9a609-122">\<system.serviceModel></span></span>](../../configure-apps/file-schema/wcf/system-servicemodel.md)
