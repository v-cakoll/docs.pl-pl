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
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: b12d5d95a17439308d79d094e8c22206778f3128
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32743254"
---
# <a name="configuring-cryptography-classes"></a>Konfigurowanie klasy kryptografii
[!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] Pozwala administratorom komputera do konfigurowania domyślne algorytmów kryptograficznych i algorytm implementacji, korzystających z programu .NET Framework i odpowiednio napisanych aplikacji.  Na przykład przedsiębiorstwo, które ma własną implementację algorytmu kryptograficznego ułatwia tę implementację domyślnego zamiast implementacji w [!INCLUDE[winsdkshort](../../../includes/winsdkshort-md.md)]. Mimo że zarządzanych aplikacji, które używają kryptografii zawsze można wybrać jawnie powiązać konkretnej implementacji, zaleca się ich tworzenie obiektów kryptograficzne przy użyciu systemu konfiguracji usług kryptograficznych.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Mapowanie nazw algorytmów na klasy kryptografii](../../../docs/framework/configure-apps/map-algorithm-names-to-cryptography-classes.md)  
 Opisuje sposób mapowania nazwy algorytmu klasy kryptografii.  
  
 [Mapowanie identyfikatorów obiektów na algorytmy kryptografii](../../../docs/framework/configure-apps/map-object-identifiers-to-cryptography-algorithms.md)  
 Opisuje sposób odwzorowywania identyfikator obiektu algorytmu kryptograficznego.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Usługi kryptograficzne](../../../docs/standard/security/cryptographic-services.md)  
 Zawiera omówienie usług kryptograficznych programu [!INCLUDE[winsdkshort](../../../includes/winsdkshort-md.md)].  
  
 [Schemat ustawień kryptografii](../../../docs/framework/configure-apps/file-schema/cryptography/index.md)  
 W tym artykule opisano elementy, które mapują algorytm przyjaznej nazwy klasy, które implementują algorytmów kryptograficznych.
