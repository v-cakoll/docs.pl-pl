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
ms.openlocfilehash: ba11eed316e227ceae4cb5acecb2b081fa8868f2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61705535"
---
# <a name="configuring-cryptography-classes"></a>Konfigurowanie klasy kryptografii
[!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] Umożliwia Administratorzy komputera skonfigurować domyślne algorytmy kryptograficzne i implementacje algorytmu, korzystających z .NET Framework i odpowiednio napisane aplikacje.  Na przykład jednostka, która ma własną implementację algorytmu kryptograficznego wprowadzić tę implementację domyślnego zamiast implementacji w [!INCLUDE[winsdkshort](../../../includes/winsdkshort-md.md)]. Mimo, że aplikacje zarządzane, które używają kryptografii zawsze można jawnie powiązać z określoną implementację, zaleca się ich tworzenia obiektów kryptograficzne przy użyciu systemu konfiguracji kryptograficznej.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Mapowanie nazw algorytmów na klasy kryptografii](../../../docs/framework/configure-apps/map-algorithm-names-to-cryptography-classes.md)  
 Opisuje sposób mapowania nazwy algorytmu na klasy kryptografii.  
  
 [Mapowanie identyfikatorów obiektów na algorytmy kryptografii](../../../docs/framework/configure-apps/map-object-identifiers-to-cryptography-algorithms.md)  
 W tym artykule opisano sposób mapowania identyfikatora obiektu na algorytm kryptograficzny.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Usługi kryptograficzne](../../../docs/standard/security/cryptographic-services.md)  
 Zawiera omówienie usług kryptograficznych programu [!INCLUDE[winsdkshort](../../../includes/winsdkshort-md.md)].  
  
 [Schemat ustawień kryptografii](../../../docs/framework/configure-apps/file-schema/cryptography/index.md)  
 W tym artykule opisano elementy, które mapują przyjazne nazwy algorytmu na klasy, które implementują algorytmy kryptograficzne.
