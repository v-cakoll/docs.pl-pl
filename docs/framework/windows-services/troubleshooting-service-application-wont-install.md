---
title: 'Rozwiązywanie problemów: aplikacja usług nie instaluje się.'
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
ms.openlocfilehash: c45ab03ec4577d88953b0e43531082a46c29e8fd
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053535"
---
# <a name="troubleshooting-service-application-wont-install"></a><span data-ttu-id="3da0c-102">Rozwiązywanie problemów: aplikacja usług nie instaluje się.</span><span class="sxs-lookup"><span data-stu-id="3da0c-102">Troubleshooting: Service Application Won't Install</span></span>
<span data-ttu-id="3da0c-103">Jeśli aplikacja usługi nie zostanie prawidłowo zainstalowana, upewnij się, że <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> właściwość klasy usługi jest ustawiona na taką samą wartość jak w instalatorze dla tej usługi.</span><span class="sxs-lookup"><span data-stu-id="3da0c-103">If your service application will not install correctly, check to make sure that the <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property for the service class is set to the same value as is shown in the installer for that service.</span></span> <span data-ttu-id="3da0c-104">Wartość musi być taka sama w obu wystąpieniach, aby można było poprawnie zainstalować usługę.</span><span class="sxs-lookup"><span data-stu-id="3da0c-104">The value must be the same in both instances in order for your service to install correctly.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3da0c-105">Możesz również zapoznać się z dziennikami instalacji, aby uzyskać informacje na temat procesu instalacji.</span><span class="sxs-lookup"><span data-stu-id="3da0c-105">You can also look at the installation logs to get feedback on the installation process.</span></span>  
  
 <span data-ttu-id="3da0c-106">Należy również sprawdzić, czy masz już zainstalowaną inną usługę o tej samej nazwie.</span><span class="sxs-lookup"><span data-stu-id="3da0c-106">You should also check to determine whether you have another service with the same name already installed.</span></span> <span data-ttu-id="3da0c-107">Aby instalacja powiodła się, nazwy usług muszą być unikatowe.</span><span class="sxs-lookup"><span data-stu-id="3da0c-107">Service names must be unique for installation to succeed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3da0c-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3da0c-108">See also</span></span>

- [<span data-ttu-id="3da0c-109">Wprowadzenie do aplikacji usług systemu Windows</span><span class="sxs-lookup"><span data-stu-id="3da0c-109">Introduction to Windows Service Applications</span></span>](introduction-to-windows-service-applications.md)
