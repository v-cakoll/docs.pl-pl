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
ms.openlocfilehash: e53f4c5c9e24fb25b43b7f27b80ab984214eeac2
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "69927774"
---
# <a name="configuring-cryptography-classes"></a><span data-ttu-id="d0b45-102">Konfigurowanie klasy kryptografii</span><span class="sxs-lookup"><span data-stu-id="d0b45-102">Configuring Cryptography Classes</span></span>
<span data-ttu-id="d0b45-103">Windows SDK pozwala administratorom komputerów skonfigurować domyślne algorytmy kryptograficzne i implementacje algorytmów, które są używane przez .NET Framework i odpowiednio pisanych aplikacje.</span><span class="sxs-lookup"><span data-stu-id="d0b45-103">The Windows SDK allows computer administrators to configure the default cryptographic algorithms and algorithm implementations that the .NET Framework and appropriately written applications use.</span></span>  <span data-ttu-id="d0b45-104">Na przykład przedsiębiorstwo, które ma własną implementację algorytmu kryptograficznego, może wprowadzić implementację domyślną zamiast implementacji w Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="d0b45-104">For example, an enterprise that has its own implementation of a cryptographic algorithm can make that implementation the default instead of the implementation shipped in the Windows SDK.</span></span> <span data-ttu-id="d0b45-105">Chociaż zarządzane aplikacje, które używają kryptografii, zawsze mogą jawnie powiązać z konkretną implementacją, zaleca się utworzenie obiektów kryptograficznych przy użyciu systemu konfiguracji kryptograficznej.</span><span class="sxs-lookup"><span data-stu-id="d0b45-105">Although managed applications that use cryptography can always choose to explicitly bind to a particular implementation, it is recommended that they create cryptographic objects by using the crypto configuration system.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d0b45-106">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="d0b45-106">In This Section</span></span>  
 [<span data-ttu-id="d0b45-107">Mapowanie nazw algorytmów na klasy kryptografii</span><span class="sxs-lookup"><span data-stu-id="d0b45-107">Mapping Algorithm Names to Cryptography Classes</span></span>](map-algorithm-names-to-cryptography-classes.md)  
 <span data-ttu-id="d0b45-108">Opisuje sposób mapowania nazwy algorytmu na klasę kryptograficzną.</span><span class="sxs-lookup"><span data-stu-id="d0b45-108">Describes how to map an algorithm name to a cryptography class.</span></span>  
  
 [<span data-ttu-id="d0b45-109">Mapowanie identyfikatorów obiektów na algorytmy kryptografii</span><span class="sxs-lookup"><span data-stu-id="d0b45-109">Mapping Object Identifiers to Cryptography Algorithms</span></span>](map-object-identifiers-to-cryptography-algorithms.md)  
 <span data-ttu-id="d0b45-110">Opisuje sposób mapowania identyfikatora obiektu na algorytm kryptografii.</span><span class="sxs-lookup"><span data-stu-id="d0b45-110">Describes how to map an object identifier to a cryptography algorithm.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="d0b45-111">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="d0b45-111">Related Sections</span></span>  
 [<span data-ttu-id="d0b45-112">Usługi kryptograficzne</span><span class="sxs-lookup"><span data-stu-id="d0b45-112">Cryptographic Services</span></span>](../../standard/security/cryptographic-services.md)  
 <span data-ttu-id="d0b45-113">Zawiera omówienie usług kryptograficznych zapewnianych przez Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="d0b45-113">Provides an overview of cryptographic services provided by the Windows SDK.</span></span>  
  
 [<span data-ttu-id="d0b45-114">Schemat ustawień kryptografii</span><span class="sxs-lookup"><span data-stu-id="d0b45-114">Cryptography Settings Schema</span></span>](./file-schema/cryptography/index.md)  
 <span data-ttu-id="d0b45-115">Opisuje elementy, które mapują przyjazne nazwy algorytmów na klasy implementujące algorytmy kryptografii.</span><span class="sxs-lookup"><span data-stu-id="d0b45-115">Describes elements that map friendly algorithm names to classes that implement cryptography algorithms.</span></span>
