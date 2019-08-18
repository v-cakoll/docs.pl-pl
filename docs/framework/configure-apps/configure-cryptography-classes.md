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
ms.openlocfilehash: 77f26405792ac782f2a04e174e8165a09b7f22f6
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/17/2019
ms.locfileid: "69567335"
---
# <a name="configuring-cryptography-classes"></a><span data-ttu-id="9bb34-102">Konfigurowanie klasy kryptografii</span><span class="sxs-lookup"><span data-stu-id="9bb34-102">Configuring Cryptography Classes</span></span>
<span data-ttu-id="9bb34-103">Windows SDK pozwala administratorom komputerów skonfigurować domyślne algorytmy kryptograficzne i implementacje algorytmów, które są używane przez .NET Framework i odpowiednio pisanych aplikacje.</span><span class="sxs-lookup"><span data-stu-id="9bb34-103">The Windows SDK allows computer administrators to configure the default cryptographic algorithms and algorithm implementations that the .NET Framework and appropriately written applications use.</span></span>  <span data-ttu-id="9bb34-104">Na przykład przedsiębiorstwo, które ma własną implementację algorytmu kryptograficznego, może wprowadzić implementację domyślną zamiast implementacji w Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="9bb34-104">For example, an enterprise that has its own implementation of a cryptographic algorithm can make that implementation the default instead of the implementation shipped in the Windows SDK.</span></span> <span data-ttu-id="9bb34-105">Chociaż zarządzane aplikacje, które używają kryptografii, zawsze mogą jawnie powiązać z konkretną implementacją, zaleca się utworzenie obiektów kryptograficznych przy użyciu systemu konfiguracji kryptograficznej.</span><span class="sxs-lookup"><span data-stu-id="9bb34-105">Although managed applications that use cryptography can always choose to explicitly bind to a particular implementation, it is recommended that they create cryptographic objects by using the crypto configuration system.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9bb34-106">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="9bb34-106">In This Section</span></span>  
 [<span data-ttu-id="9bb34-107">Mapowanie nazw algorytmów na klasy kryptografii</span><span class="sxs-lookup"><span data-stu-id="9bb34-107">Mapping Algorithm Names to Cryptography Classes</span></span>](../../../docs/framework/configure-apps/map-algorithm-names-to-cryptography-classes.md)  
 <span data-ttu-id="9bb34-108">Opisuje sposób mapowania nazwy algorytmu na klasę kryptograficzną.</span><span class="sxs-lookup"><span data-stu-id="9bb34-108">Describes how to map an algorithm name to a cryptography class.</span></span>  
  
 [<span data-ttu-id="9bb34-109">Mapowanie identyfikatorów obiektów na algorytmy kryptografii</span><span class="sxs-lookup"><span data-stu-id="9bb34-109">Mapping Object Identifiers to Cryptography Algorithms</span></span>](../../../docs/framework/configure-apps/map-object-identifiers-to-cryptography-algorithms.md)  
 <span data-ttu-id="9bb34-110">Opisuje sposób mapowania identyfikatora obiektu na algorytm kryptografii.</span><span class="sxs-lookup"><span data-stu-id="9bb34-110">Describes how to map an object identifier to a cryptography algorithm.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="9bb34-111">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="9bb34-111">Related Sections</span></span>  
 [<span data-ttu-id="9bb34-112">Usługi kryptograficzne</span><span class="sxs-lookup"><span data-stu-id="9bb34-112">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)  
 <span data-ttu-id="9bb34-113">Zawiera omówienie usług kryptograficznych zapewnianych przez Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="9bb34-113">Provides an overview of cryptographic services provided by the Windows SDK.</span></span>  
  
 [<span data-ttu-id="9bb34-114">Schemat ustawień kryptografii</span><span class="sxs-lookup"><span data-stu-id="9bb34-114">Cryptography Settings Schema</span></span>](../../../docs/framework/configure-apps/file-schema/cryptography/index.md)  
 <span data-ttu-id="9bb34-115">Opisuje elementy, które mapują przyjazne nazwy algorytmów na klasy implementujące algorytmy kryptografii.</span><span class="sxs-lookup"><span data-stu-id="9bb34-115">Describes elements that map friendly algorithm names to classes that implement cryptography algorithms.</span></span>
