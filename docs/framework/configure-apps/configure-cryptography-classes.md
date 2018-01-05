---
title: Konfigurowanie klasy kryptografii
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuration files [.NET Framework], cryptography
- cryptographic algorithms
- security [.NET Framework], encryption
- cryptography, classes
- .NET Framework application configuration, cryptography
- default cryptography
ms.assetid: eee3ccb8-2c0d-4f35-b38d-6892a46c14e5
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 23bd6007beb870895316a565283ee7e7354c931b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="configuring-cryptography-classes"></a><span data-ttu-id="fd908-102">Konfigurowanie klasy kryptografii</span><span class="sxs-lookup"><span data-stu-id="fd908-102">Configuring Cryptography Classes</span></span>
<span data-ttu-id="fd908-103">[!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] Pozwala administratorom komputera do konfigurowania domyślne algorytmów kryptograficznych i algorytm implementacji, korzystających z programu .NET Framework i odpowiednio napisanych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="fd908-103">The [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] allows computer administrators to configure the default cryptographic algorithms and algorithm implementations that the .NET Framework and appropriately written applications use.</span></span>  <span data-ttu-id="fd908-104">Na przykład przedsiębiorstwo, które ma własną implementację algorytmu kryptograficznego ułatwia tę implementację domyślnego zamiast implementacji w [!INCLUDE[winsdkshort](../../../includes/winsdkshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fd908-104">For example, an enterprise that has its own implementation of a cryptographic algorithm can make that implementation the default instead of the implementation shipped in the [!INCLUDE[winsdkshort](../../../includes/winsdkshort-md.md)].</span></span> <span data-ttu-id="fd908-105">Mimo że zarządzanych aplikacji, które używają kryptografii zawsze można wybrać jawnie powiązać konkretnej implementacji, zaleca się ich tworzenie obiektów kryptograficzne przy użyciu systemu konfiguracji usług kryptograficznych.</span><span class="sxs-lookup"><span data-stu-id="fd908-105">Although managed applications that use cryptography can always choose to explicitly bind to a particular implementation, it is recommended that they create cryptographic objects by using the crypto configuration system.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fd908-106">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="fd908-106">In This Section</span></span>  
 [<span data-ttu-id="fd908-107">Mapowanie nazw algorytmów na klasy kryptografii</span><span class="sxs-lookup"><span data-stu-id="fd908-107">Mapping Algorithm Names to Cryptography Classes</span></span>](../../../docs/framework/configure-apps/map-algorithm-names-to-cryptography-classes.md)  
 <span data-ttu-id="fd908-108">Opisuje sposób mapowania nazwy algorytmu klasy kryptografii.</span><span class="sxs-lookup"><span data-stu-id="fd908-108">Describes how to map an algorithm name to a cryptography class.</span></span>  
  
 [<span data-ttu-id="fd908-109">Mapowanie identyfikatorów obiektów na algorytmy kryptografii</span><span class="sxs-lookup"><span data-stu-id="fd908-109">Mapping Object Identifiers to Cryptography Algorithms</span></span>](../../../docs/framework/configure-apps/map-object-identifiers-to-cryptography-algorithms.md)  
 <span data-ttu-id="fd908-110">Opisuje sposób odwzorowywania identyfikator obiektu algorytmu kryptograficznego.</span><span class="sxs-lookup"><span data-stu-id="fd908-110">Describes how to map an object identifier to a cryptography algorithm.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="fd908-111">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="fd908-111">Related Sections</span></span>  
 [<span data-ttu-id="fd908-112">Usługi kryptograficzne</span><span class="sxs-lookup"><span data-stu-id="fd908-112">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)  
 <span data-ttu-id="fd908-113">Zawiera omówienie usług kryptograficznych programu [!INCLUDE[winsdkshort](../../../includes/winsdkshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fd908-113">Provides an overview of cryptographic services provided by the [!INCLUDE[winsdkshort](../../../includes/winsdkshort-md.md)].</span></span>  
  
 [<span data-ttu-id="fd908-114">Schemat ustawień kryptografii</span><span class="sxs-lookup"><span data-stu-id="fd908-114">Cryptography Settings Schema</span></span>](../../../docs/framework/configure-apps/file-schema/cryptography/index.md)  
 <span data-ttu-id="fd908-115">W tym artykule opisano elementy, które mapują algorytm przyjaznej nazwy klasy, które implementują algorytmów kryptograficznych.</span><span class="sxs-lookup"><span data-stu-id="fd908-115">Describes elements that map friendly algorithm names to classes that implement cryptography algorithms.</span></span>
