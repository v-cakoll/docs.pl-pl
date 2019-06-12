---
title: Konfigurowanie klasy kryptografii
ms.date: 03/30/2017
helpviewer_keywords:
- configuration files [.NET Framework], cryptography
- cryptographic algorithms
- security [.NET Framework], encryption
- cryptography, classes
- .NET Framework application configuration, cryptography
- default cryptography
ms.assetid: eee3ccb8-2c0d-4f35-b38d-6892a46c14e5
ms.openlocfilehash: 23bf831a4374add55258f5fb41c17a5d4a8f14c3
ms.sourcegitcommit: 34593b4d0be779699d38a9949d6aec11561657ec
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/11/2019
ms.locfileid: "66832811"
---
# <a name="configuring-cryptography-classes"></a><span data-ttu-id="52491-102">Konfigurowanie klasy kryptografii</span><span class="sxs-lookup"><span data-stu-id="52491-102">Configuring Cryptography Classes</span></span>
<span data-ttu-id="52491-103">Zestaw Windows Software Development Kit (SDK) umożliwia administratorom komputera skonfigurować domyślne algorytmy kryptograficzne i implementacje algorytmu, korzystających z .NET Framework i odpowiednio napisane aplikacje.</span><span class="sxs-lookup"><span data-stu-id="52491-103">The Windows Software Development Kit (SDK) allows computer administrators to configure the default cryptographic algorithms and algorithm implementations that the .NET Framework and appropriately written applications use.</span></span>  <span data-ttu-id="52491-104">Na przykład jednostka, która ma własną implementację algorytmu kryptograficznego ułatwia tę implementację domyślnego zamiast wykonania dostarczane w zestawie Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="52491-104">For example, an enterprise that has its own implementation of a cryptographic algorithm can make that implementation the default instead of the implementation shipped in the Windows SDK.</span></span> <span data-ttu-id="52491-105">Mimo, że aplikacje zarządzane, które używają kryptografii zawsze można jawnie powiązać z określoną implementację, zaleca się ich tworzenia obiektów kryptograficzne przy użyciu systemu konfiguracji kryptograficznej.</span><span class="sxs-lookup"><span data-stu-id="52491-105">Although managed applications that use cryptography can always choose to explicitly bind to a particular implementation, it is recommended that they create cryptographic objects by using the crypto configuration system.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="52491-106">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="52491-106">In This Section</span></span>  
 [<span data-ttu-id="52491-107">Mapowanie nazw algorytmów na klasy kryptografii</span><span class="sxs-lookup"><span data-stu-id="52491-107">Mapping Algorithm Names to Cryptography Classes</span></span>](../../../docs/framework/configure-apps/map-algorithm-names-to-cryptography-classes.md)  
 <span data-ttu-id="52491-108">Opisuje sposób mapowania nazwy algorytmu na klasy kryptografii.</span><span class="sxs-lookup"><span data-stu-id="52491-108">Describes how to map an algorithm name to a cryptography class.</span></span>  
  
 [<span data-ttu-id="52491-109">Mapowanie identyfikatorów obiektów na algorytmy kryptografii</span><span class="sxs-lookup"><span data-stu-id="52491-109">Mapping Object Identifiers to Cryptography Algorithms</span></span>](../../../docs/framework/configure-apps/map-object-identifiers-to-cryptography-algorithms.md)  
 <span data-ttu-id="52491-110">W tym artykule opisano sposób mapowania identyfikatora obiektu na algorytm kryptograficzny.</span><span class="sxs-lookup"><span data-stu-id="52491-110">Describes how to map an object identifier to a cryptography algorithm.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="52491-111">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="52491-111">Related Sections</span></span>  
 [<span data-ttu-id="52491-112">Usługi kryptograficzne</span><span class="sxs-lookup"><span data-stu-id="52491-112">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)  
 <span data-ttu-id="52491-113">Omówienie usługi kryptograficzne, dostarczone przez zestaw Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="52491-113">Provides an overview of cryptographic services provided by the Windows SDK.</span></span>  
  
 [<span data-ttu-id="52491-114">Schemat ustawień kryptografii</span><span class="sxs-lookup"><span data-stu-id="52491-114">Cryptography Settings Schema</span></span>](../../../docs/framework/configure-apps/file-schema/cryptography/index.md)  
 <span data-ttu-id="52491-115">W tym artykule opisano elementy, które mapują przyjazne nazwy algorytmu na klasy, które implementują algorytmy kryptograficzne.</span><span class="sxs-lookup"><span data-stu-id="52491-115">Describes elements that map friendly algorithm names to classes that implement cryptography algorithms.</span></span>
