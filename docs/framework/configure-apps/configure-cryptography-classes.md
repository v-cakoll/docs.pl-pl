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
# <a name="configuring-cryptography-classes"></a>Konfigurowanie klasy kryptografii
Zestaw Windows Software Development Kit (SDK) umożliwia administratorom komputera skonfigurować domyślne algorytmy kryptograficzne i implementacje algorytmu, korzystających z .NET Framework i odpowiednio napisane aplikacje.  Na przykład jednostka, która ma własną implementację algorytmu kryptograficznego ułatwia tę implementację domyślnego zamiast wykonania dostarczane w zestawie Windows SDK. Mimo, że aplikacje zarządzane, które używają kryptografii zawsze można jawnie powiązać z określoną implementację, zaleca się ich tworzenia obiektów kryptograficzne przy użyciu systemu konfiguracji kryptograficznej.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Mapowanie nazw algorytmów na klasy kryptografii](../../../docs/framework/configure-apps/map-algorithm-names-to-cryptography-classes.md)  
 Opisuje sposób mapowania nazwy algorytmu na klasy kryptografii.  
  
 [Mapowanie identyfikatorów obiektów na algorytmy kryptografii](../../../docs/framework/configure-apps/map-object-identifiers-to-cryptography-algorithms.md)  
 W tym artykule opisano sposób mapowania identyfikatora obiektu na algorytm kryptograficzny.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Usługi kryptograficzne](../../../docs/standard/security/cryptographic-services.md)  
 Omówienie usługi kryptograficzne, dostarczone przez zestaw Windows SDK.  
  
 [Schemat ustawień kryptografii](../../../docs/framework/configure-apps/file-schema/cryptography/index.md)  
 W tym artykule opisano elementy, które mapują przyjazne nazwy algorytmu na klasy, które implementują algorytmy kryptograficzne.
