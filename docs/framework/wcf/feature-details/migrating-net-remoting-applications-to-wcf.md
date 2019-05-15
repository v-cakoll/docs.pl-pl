---
title: Migrowanie aplikacji usług zdalnych platformy .NET do programu WCF
ms.date: 03/30/2017
helpviewer_keywords:
- ',NET remoting [WCF]'
ms.assetid: 24793465-65ae-4308-8c12-dce4fd12a583
ms.openlocfilehash: c0ce7c9badc8bad6eedc58827b6efe2595ab2cf8
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65592867"
---
# <a name="migrating-net-remoting-applications-to-wcf"></a><span data-ttu-id="b9675-102">Migrowanie aplikacji usług zdalnych platformy .NET do programu WCF</span><span class="sxs-lookup"><span data-stu-id="b9675-102">Migrating .NET Remoting Applications to WCF</span></span>
<span data-ttu-id="b9675-103">**Ten temat dotyczy technologią starszą, która została zachowana na potrzeby zgodności z poprzednimi wersjami z istniejącymi aplikacjami i nie jest zalecane w przypadku nowych wdrożeń. Teraz należy opracować aplikacje rozproszone przy użyciu usługi WCF.**</span><span class="sxs-lookup"><span data-stu-id="b9675-103">**This topic is specific to a legacy technology that is retained for backward compatibility with existing applications and is not recommended for new development. Distributed applications should now be developed using WCF.**</span></span>  
  
 <span data-ttu-id="b9675-104">Istnieją dwa sposoby, aby móc korzystać z usługi WCF z istniejącymi aplikacjami wywołaniem funkcji zdalnych .NET: integracji i migracji.</span><span class="sxs-lookup"><span data-stu-id="b9675-104">There are two ways to take advantage of WCF with existing .NET Remoting applications: integration and migration.</span></span> <span data-ttu-id="b9675-105">Integracja umożliwia wywołaniem funkcji zdalnych .NET w wersji 2.0 i usługi WCF działa obok siebie, co pozwala na udostępnianie tych samych obiektów firmy za pośrednictwem obie technologie jednocześnie bez konieczności modyfikowania istniejącego kodu wywołaniem funkcji zdalnych .NET w wersji 2.0.</span><span class="sxs-lookup"><span data-stu-id="b9675-105">Integration allows you to have .NET Remoting 2.0 and WCF running side by side, letting you expose the same business objects over both technologies simultaneously without having to modify your existing .NET Remoting 2.0 code.</span></span> <span data-ttu-id="b9675-106">Integracja wymaga, że są uruchomione na .NET Framework 2.0 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="b9675-106">Integration requires that you are running on .NET Framework 2.0 or greater.</span></span> <span data-ttu-id="b9675-107">Jeśli chcesz korzystać z funkcji WCF i nie ma potrzeby o komunikacji sieciowej zgodność z systemami komunikacji zdalnej w wersji 2.0, należy przeprowadzić migrację całej usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="b9675-107">If you want to take advantage of WCF features and do not need wire compatibility with Remoting 2.0 systems, you can migrate your entire service to WCF.</span></span> <span data-ttu-id="b9675-108">Migracja z wywołaniem funkcji zdalnych .NET w wersji 2.0 do programu WCF wymaga wprowadzenia zmian do obiektu zdalnego interfejsu i jego ustawienia konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="b9675-108">Migration from .NET Remoting 2.0 to WCF requires changes to the remote object's interface and its configuration settings.</span></span> <span data-ttu-id="b9675-109">Oba te tematy zostały uwzględnione w [z wywołaniem funkcji zdalnych do programu Windows Communication Foundation](https://go.microsoft.com/fwlink/?LinkId=74403).</span><span class="sxs-lookup"><span data-stu-id="b9675-109">Both of these topics are covered in [From Remoting to the Windows Communication Foundation](https://go.microsoft.com/fwlink/?LinkId=74403).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9675-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b9675-110">See also</span></span>

- [<span data-ttu-id="b9675-111">Omówienie pojęć</span><span class="sxs-lookup"><span data-stu-id="b9675-111">Conceptual Overview</span></span>](../../../../docs/framework/wcf/conceptual-overview.md)
