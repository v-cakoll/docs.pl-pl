---
title: "Mieszanie protokołów zaufania w scenariuszach obejmujących federację"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d7b5fee9-2246-4b09-b8d7-9e63cb817279
caps.latest.revision: "7"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 7031e222b152bfa61e13e0e4a44b5ad9418b07c9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="mixing-trust-protocols-in-federated-scenarios"></a>Mieszanie protokołów zaufania w scenariuszach obejmujących federację
Może to być scenariuszy w których federacyjnych klienci komunikują się z usługą i tokenu usługa zabezpieczenia (STS), które nie mają tej samej wersji zaufania. Usługa może zawierać WSDL `RequestSecurityTokenTemplate` potwierdzenia z elementami WS-Trust, które są w różnych wersjach niż Usługa tokenu Zabezpieczającego. W takich przypadkach [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] klienta konwertuje elementy WS-Trust otrzymanych od `RequestSecurityTokenTemplate` zgodna wersja zaufania usługi STS. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]uchwyty niezgodne wersje zaufania tylko dla powiązań standardowych. Wszystkie parametry standard — algorytm, które są rozpoznawane przez [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] są częścią standardowej powiązania. W tym temacie opisano [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zachowanie w przypadku różnych zaufania ustawienia między usługą i Usługa tokenu Zabezpieczającego.  
  
## <a name="rp-feb-2005-and-sts-feb-2005"></a>RP luty 2005 i STS luty 2005  
 WSDL dla jednostki uzależnionej strony (RP) zawiera następujące elementy w ramach `RequestSecurityTokenTemplate` sekcji:  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
 Plik konfiguracji klienta zawiera listę parametrów.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Nie można rozróżnianie między klientem a usługą parametrów; dodaje wszystkie parametry i wysyła je w `RequestSecurityTokenTemplate` (RST).  
  
## <a name="rp-trust-13-and-sts-trust-13"></a>Zaufanie RP 1.3 i zaufania STS 1.3  
 WSDL dla planu odzyskiwania zawiera następujące elementy w ramach `RequestSecurityTokenTemplate` sekcji:  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
-   `KeyWrapAlgorithm`  
  
 Plik konfiguracji klienta zawiera `secondaryParameters` element, który opakowuje parametrów określonych przez planu odzyskiwania.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Usuwa `EncryptionAlgorithm`, `CanonicalizationAlgorithm` i `KeyWrapAlgorithm` elementy z elementu najwyższego poziomu w obszarze RST, jeśli są one obecne w `SecondaryParameters` elementu. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]dołącza `SecondaryParameters` elementu RST wychodzących, nie mają być modyfikowane.  
  
## <a name="rp-trust-feb-2005-and-sts-trust-13"></a>Zaufanie RP luty 2005 i zaufania STS 1.3  
 WSDL dla planu odzyskiwania zawiera następujące elementy w `RequestSecurityTokenTemplate` sekcji:  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
 Plik konfiguracji klienta zawiera listę parametrów.  
  
 W pliku konfiguracji klienta [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] nie rozróżnianie między parametrami usługi i klienta. W związku z tym [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] konwertuje wszystkie parametry do przestrzeni nazw w wersji 1.3 zaufania.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]uchwyty `KeyType`, `KeySize`, i `TokenType` elementy w następujący sposób:  
  
-   Pobieranie pliku WSDL, utwórz powiązanie i przypisz `KeyType`, `KeySize`, i `TokenType` z parametrów planu odzyskiwania. Następnie zostanie wygenerowany plik konfiguracji klienta.  
  
-   Klienta można teraz zmienić żadnego parametru w pliku konfiguracji.  
  
-   W czasie wykonywania [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kopiuje wszystkie parametry określonego do `AdditionalTokenParameters` sekcji pliku konfiguracji klienta, z wyjątkiem `KeyType`, `KeySize` i `TokenType`, ponieważ te parametry są wyjaśnić podczas konfiguracji Generowanie pliku.  
  
## <a name="rp-trust-13-and-sts-trust-feb-2005"></a>Zaufanie RP 1.3 i zaufania STS luty 2005  
 WSDL dla planu odzyskiwania zawiera następujące elementy w `RequestSecurityTokenTemplate` sekcji:  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
-   `KeyWrapAlgorithm`  
  
 Plik konfiguracji klienta zawiera `secondaryParamters` element, który opakowuje parametrów określonych przez planu odzyskiwania.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]kopiuje wszystkie parametry, które są określone w `SecondaryParameters` sekcji, aby element RST najwyższego poziomu, ale nie konwertuje je do przestrzeni nazw protokołu WS-Trust 2005.
