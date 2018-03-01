---
title: "Migrowanie aplikacji usług zdalnych platformy .NET do programu WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ',NET remoting [WCF]'
ms.assetid: 24793465-65ae-4308-8c12-dce4fd12a583
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b7d305adf1810832016cdafbb60fc025f17e0786
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="migrating-net-remoting-applications-to-wcf"></a><span data-ttu-id="52b52-102">Migrowanie aplikacji usług zdalnych platformy .NET do programu WCF</span><span class="sxs-lookup"><span data-stu-id="52b52-102">Migrating .NET Remoting Applications to WCF</span></span>
<span data-ttu-id="52b52-103">**Ten temat dotyczy starszych technologia, która została zachowana na potrzeby zgodności z poprzednimi wersjami z istniejącymi aplikacjami i nie jest zalecane w przypadku nowych wdrożeń. Teraz należy opracować aplikacji rozproszonych za pomocą [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].**</span><span class="sxs-lookup"><span data-stu-id="52b52-103">**This topic is specific to a legacy technology that is retained for backward compatibility with existing applications and is not recommended for new development. Distributed applications should now be developed using [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].**</span></span>  
  
 <span data-ttu-id="52b52-104">Istnieją dwa sposoby, aby móc korzystać z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] z istniejących aplikacji .NET Remoting: integracja i migracji.</span><span class="sxs-lookup"><span data-stu-id="52b52-104">There are two ways to take advantage of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] with existing .NET Remoting applications: integration and migration.</span></span> <span data-ttu-id="52b52-105">Integracji pozwala na program .net Remoting 2.0 i [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] działa obok siebie, dzięki czemu naraża te same obiekty biznesowych w obu tych technologii jednocześnie bez konieczności modyfikowania Twoje istniejące .net Remoting 2.0 kodu.</span><span class="sxs-lookup"><span data-stu-id="52b52-105">Integration allows you to have .Net Remoting 2.0 and [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] running side by side, letting you expose the same business objects over both technologies simultaneously without having to modify your existing .Net Remoting 2.0 code.</span></span> <span data-ttu-id="52b52-106">Integracja wymaga się, że są uruchomione na [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 2.0 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="52b52-106">Integration requires that you are running on [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 2.0 or greater.</span></span> <span data-ttu-id="52b52-107">Jeśli chcesz móc korzystać z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] funkcje i czy nie wymagają okablować zgodność z systemów zdalnych 2.0, można migrować całą usługa [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="52b52-107">If you want to take advantage of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] features and do not need wire compatibility with Remoting 2.0 systems, you can migrate your entire service to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span> <span data-ttu-id="52b52-108">Migracja z usług zdalnych .NET 2.0 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] wymaga wprowadzenia zmian obiektu zdalnego interfejsu i jego ustawień konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="52b52-108">Migration from .NET Remoting 2.0 to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] requires changes to the remote object's interface and its configuration settings.</span></span> <span data-ttu-id="52b52-109">Oba te tematy zostały omówione w [z Remoting do programu Windows Communication Foundation](http://go.microsoft.com/fwlink/?LinkId=74403).</span><span class="sxs-lookup"><span data-stu-id="52b52-109">Both of these topics are covered in [From Remoting to the Windows Communication Foundation](http://go.microsoft.com/fwlink/?LinkId=74403).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52b52-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="52b52-110">See Also</span></span>  
 [<span data-ttu-id="52b52-111">Omówienie pojęć</span><span class="sxs-lookup"><span data-stu-id="52b52-111">Conceptual Overview</span></span>](../../../../docs/framework/wcf/conceptual-overview.md)
