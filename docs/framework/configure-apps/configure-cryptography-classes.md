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
# <a name="configuring-cryptography-classes"></a>Konfigurowanie klasy kryptografii
Windows SDK pozwala administratorom komputerów skonfigurować domyślne algorytmy kryptograficzne i implementacje algorytmów, które są używane przez .NET Framework i odpowiednio pisanych aplikacje.  Na przykład przedsiębiorstwo, które ma własną implementację algorytmu kryptograficznego, może wprowadzić implementację domyślną zamiast implementacji w Windows SDK. Chociaż zarządzane aplikacje, które używają kryptografii, zawsze mogą jawnie powiązać z konkretną implementacją, zaleca się utworzenie obiektów kryptograficznych przy użyciu systemu konfiguracji kryptograficznej.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Mapowanie nazw algorytmów na klasy kryptografii](map-algorithm-names-to-cryptography-classes.md)  
 Opisuje sposób mapowania nazwy algorytmu na klasę kryptograficzną.  
  
 [Mapowanie identyfikatorów obiektów na algorytmy kryptografii](map-object-identifiers-to-cryptography-algorithms.md)  
 Opisuje sposób mapowania identyfikatora obiektu na algorytm kryptografii.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Usługi kryptograficzne](../../standard/security/cryptographic-services.md)  
 Zawiera omówienie usług kryptograficznych zapewnianych przez Windows SDK.  
  
 [Schemat ustawień kryptografii](./file-schema/cryptography/index.md)  
 Opisuje elementy, które mapują przyjazne nazwy algorytmów na klasy implementujące algorytmy kryptografii.
