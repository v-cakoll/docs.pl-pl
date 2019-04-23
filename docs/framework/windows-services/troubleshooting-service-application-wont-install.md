---
title: 'Rozwiązywanie problemów: Aplikacja usług nie instaluje się'
ms.date: 03/30/2017
helpviewer_keywords:
- troubleshooting service applications
- services, troubleshooting
- services, debugging
- Windows NT services, troubleshooting
- troubleshooting NT services
- Windows Service applications, troubleshooting
ms.assetid: 45c48e2e-b97d-44bc-8896-14f328e0ce33
author: ghogen
ms.openlocfilehash: f75a2f33ecde408d2d8e2f2343197ba56c4b8c21
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59143822"
---
# <a name="troubleshooting-service-application-wont-install"></a><span data-ttu-id="e7163-102">Rozwiązywanie problemów: Aplikacja usług nie instaluje się</span><span class="sxs-lookup"><span data-stu-id="e7163-102">Troubleshooting: Service Application Won't Install</span></span>
<span data-ttu-id="e7163-103">Jeśli Twoja aplikacja usługi nie zainstaluje się poprawnie, sprawdź, upewnij się, że <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> właściwość klasy usługi jest ustawiona na tę samą wartość, pokazane w Instalatorze za daną usługę.</span><span class="sxs-lookup"><span data-stu-id="e7163-103">If your service application will not install correctly, check to make sure that the <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property for the service class is set to the same value as is shown in the installer for that service.</span></span> <span data-ttu-id="e7163-104">Wartość musi być taka sama w obu przypadkach, w kolejności dla usługi w taki sposób poprawnie zainstalować.</span><span class="sxs-lookup"><span data-stu-id="e7163-104">The value must be the same in both instances in order for your service to install correctly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e7163-105">Można również przeglądać dzienniki instalacji, aby uzyskać opinie na temat procesu instalacji.</span><span class="sxs-lookup"><span data-stu-id="e7163-105">You can also look at the installation logs to get feedback on the installation process.</span></span>  
  
 <span data-ttu-id="e7163-106">Również należy sprawdzić, czy masz inną usługę o takiej samej nazwie już zainstalowane.</span><span class="sxs-lookup"><span data-stu-id="e7163-106">You should also check to determine whether you have another service with the same name already installed.</span></span> <span data-ttu-id="e7163-107">Nazwy usług musi być unikatowa instalacja się powiodła.</span><span class="sxs-lookup"><span data-stu-id="e7163-107">Service names must be unique for installation to succeed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7163-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e7163-108">See also</span></span>

- [<span data-ttu-id="e7163-109">Wprowadzenie do aplikacji usług systemu Windows</span><span class="sxs-lookup"><span data-stu-id="e7163-109">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
