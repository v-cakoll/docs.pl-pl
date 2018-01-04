---
title: Uruchom .NET Framework 1.1 aplikacji w systemie Windows 8, Windows 8.1 lub Windows 10
ms.custom: 
ms.date: 05/26/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows 8, running .NET Framework 1.1 apps
- .NET Framework 1.1, running on Windows 8
ms.assetid: fb14e195-fea5-4561-b9a8-60a67283edb9
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9d5b99390e62984b37b0d7267c40b1221f556f60
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="run-net-framework-11-apps-on-windows-8-windows-81-or-windows-10"></a><span data-ttu-id="6b71f-102">Uruchom .NET Framework 1.1 aplikacji w systemie Windows 8, Windows 8.1 lub Windows 10</span><span class="sxs-lookup"><span data-stu-id="6b71f-102">Run .NET Framework 1.1 apps on Windows 8, Windows 8.1, or Windows 10</span></span>

<span data-ttu-id="6b71f-103">.NET Framework 1.1 nie jest obsługiwana w [!INCLUDE[win8](../../../includes/win8-md.md)], [!INCLUDE[win81](../../../includes/win81-md.md)], [!INCLUDE[winserver8](../../../includes/winserver8-md.md)], [!INCLUDE[winblue_server_2](../../../includes/winblue-server-2-md.md)], lub w systemach operacyjnych Windows 10.</span><span class="sxs-lookup"><span data-stu-id="6b71f-103">The .NET Framework 1.1 is not supported on the [!INCLUDE[win8](../../../includes/win8-md.md)], [!INCLUDE[win81](../../../includes/win81-md.md)], [!INCLUDE[winserver8](../../../includes/winserver8-md.md)], [!INCLUDE[winblue_server_2](../../../includes/winblue-server-2-md.md)], or the Windows 10 operating systems.</span></span> <span data-ttu-id="6b71f-104">W niektórych przypadkach, .NET Framework 1.1 zostanie dokładnie zidentyfikowana jako wymagane do uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6b71f-104">In some cases, the .NET Framework 1.1 is specifically identified as required for an app to run.</span></span> <span data-ttu-id="6b71f-105">W takich przypadkach należy skontaktować się z niezależnego dostawcy oprogramowania (ISV) aplikacjami uaktualniony do uruchamiania na [!INCLUDE[net_v35SP1_short](../../../includes/net-v35sp1-short-md.md)] lub nowszej wersji.</span><span class="sxs-lookup"><span data-stu-id="6b71f-105">In those cases, you should contact your independent software vendor (ISV) to have the app upgraded to run on the [!INCLUDE[net_v35SP1_short](../../../includes/net-v35sp1-short-md.md)] or later version.</span></span> <span data-ttu-id="6b71f-106">Aby uzyskać dodatkowe informacje, zobacz [Migrowanie z programu .NET Framework 1.1](../../../docs/framework/migration-guide/migrating-from-the-net-framework-1-1.md).</span><span class="sxs-lookup"><span data-stu-id="6b71f-106">For additional information, see [Migrating from the .NET Framework 1.1](../../../docs/framework/migration-guide/migrating-from-the-net-framework-1-1.md).</span></span>

## <a name="install-the-net-framework-11-from-a-cd-or-download-center"></a><span data-ttu-id="6b71f-107">Zainstaluj program .NET Framework 1.1 z dysku CD lub Centrum pobierania</span><span class="sxs-lookup"><span data-stu-id="6b71f-107">Install the .NET Framework 1.1 from a CD or Download Center</span></span>

<span data-ttu-id="6b71f-108">Nie można ręcznie zainstalować program .NET Framework 1.1 na [!INCLUDE[win8](../../../includes/win8-md.md)], [!INCLUDE[win81](../../../includes/win81-md.md)], [!INCLUDE[winserver8](../../../includes/winserver8-md.md)], [!INCLUDE[winblue_server_2](../../../includes/winblue-server-2-md.md)], lub Windows 10.</span><span class="sxs-lookup"><span data-stu-id="6b71f-108">It isn't possible to manually install the .NET Framework 1.1 on [!INCLUDE[win8](../../../includes/win8-md.md)], [!INCLUDE[win81](../../../includes/win81-md.md)], [!INCLUDE[winserver8](../../../includes/winserver8-md.md)], [!INCLUDE[winblue_server_2](../../../includes/winblue-server-2-md.md)], or Windows 10.</span></span> <span data-ttu-id="6b71f-109">Nie jest już obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="6b71f-109">It is no longer supported.</span></span> <span data-ttu-id="6b71f-110">Jeśli spróbujesz zainstalować pakiet, zostanie wyświetlony następujący komunikat o błędzie: "Instalator nie może kontynuować, ponieważ ta wersja programu .NET Framework jest niezgodna z zainstalowaną wcześniej."</span><span class="sxs-lookup"><span data-stu-id="6b71f-110">If you try to install the package, the following error message is displayed: "Setup cannot continue because this version of the .NET Framework is incompatible with a previously installed one."</span></span> <span data-ttu-id="6b71f-111">Aby rozwiązać ten problem, zainstaluj [.NET Framework 3.5 SP1](http://www.microsoft.com/download/details.aspx?id=22).</span><span class="sxs-lookup"><span data-stu-id="6b71f-111">To solve this problem, install the [.NET Framework 3.5 SP1](http://www.microsoft.com/download/details.aspx?id=22).</span></span> <span data-ttu-id="6b71f-112">Ta wersja zawiera programu .NET Framework 2.0 (wersję, która wykonuje programu .NET Framework 1.1), który jest obsługiwany w [!INCLUDE[win8](../../../includes/win8-md.md)], [!INCLUDE[win81](../../../includes/win81-md.md)]i Windows 10.</span><span class="sxs-lookup"><span data-stu-id="6b71f-112">This version includes the .NET Framework 2.0 (the release that follows the .NET Framework 1.1), which is supported on [!INCLUDE[win8](../../../includes/win8-md.md)], [!INCLUDE[win81](../../../includes/win81-md.md)], and Windows 10.</span></span> <span data-ttu-id="6b71f-113">Zawsze należy dążyć do zainstalowania aplikacji, aby ustalić, czy jego zostaną automatycznie zaktualizowane do nowszej wersji programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6b71f-113">You should always try to install the app first to determine if it will automatically be updated to a later version of the .NET Framework.</span></span> <span data-ttu-id="6b71f-114">Jeśli nie, skontaktuj się z Twojej niezależnego dostawcy oprogramowania w celu aktualizacji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6b71f-114">If it does not, contact your ISV for an app update.</span></span>

## <a name="see-also"></a><span data-ttu-id="6b71f-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6b71f-115">See also</span></span>

<span data-ttu-id="6b71f-116">[Migrowanie z programu .NET Framework 1.1](../../../docs/framework/migration-guide/migrating-from-the-net-framework-1-1.md)
[Zainstaluj program .NET Framework 3.5 w systemie Windows 10, Windows 8.1 i Windows 8](../../../docs/framework/install/dotnet-35-windows-10.md)</span><span class="sxs-lookup"><span data-stu-id="6b71f-116">[Migrating from the .NET Framework 1.1](../../../docs/framework/migration-guide/migrating-from-the-net-framework-1-1.md)
[Install the .NET Framework 3.5 on Windows 10, Windows 8.1, and Windows 8](../../../docs/framework/install/dotnet-35-windows-10.md)</span></span>
