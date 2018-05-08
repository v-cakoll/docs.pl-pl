---
title: Mieszanie protokołów zaufania w scenariuszach obejmujących federację
ms.date: 03/30/2017
ms.assetid: d7b5fee9-2246-4b09-b8d7-9e63cb817279
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: bca23ba16c69c6d21ed7cf49aaebb8d2ed079f5e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="mixing-trust-protocols-in-federated-scenarios"></a>Mieszanie protokołów zaufania w scenariuszach obejmujących federację
Może to być scenariuszy w których federacyjnych klienci komunikują się z usługą i tokenu usługa zabezpieczenia (STS), które nie mają tej samej wersji zaufania. Usługa może zawierać WSDL `RequestSecurityTokenTemplate` potwierdzenia z elementami WS-Trust, które są w różnych wersjach niż Usługa tokenu Zabezpieczającego. W takich przypadkach klient usługi Windows Communication Foundation (WCF) konwertuje elementy WS-Trust otrzymanych od `RequestSecurityTokenTemplate` zgodna wersja zaufania usługi STS. Usługi WCF obsługuje wersje niedopasowanych zaufania tylko dla powiązań standardowych. Wszystkie parametry standard — algorytm, które są rozpoznawane przez WCF są częścią Powiązanie standardowe. W tym temacie opisano zachowanie WCF z różnymi ustawieniami relacji zaufania między usługą i Usługa tokenu Zabezpieczającego.  
  
## <a name="rp-feb-2005-and-sts-feb-2005"></a>RP luty 2005 i STS luty 2005  
 WSDL dla jednostki uzależnionej strony (RP) zawiera następujące elementy w ramach `RequestSecurityTokenTemplate` sekcji:  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
 Plik konfiguracji klienta zawiera listę parametrów.  
  
 Usługi WCF nie rozróżnianie między klientem a usługą parametrów; dodaje wszystkie parametry i wysyła je w `RequestSecurityTokenTemplate` (RST).  
  
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
  
 Usuwa WCF `EncryptionAlgorithm`, `CanonicalizationAlgorithm` i `KeyWrapAlgorithm` elementy z elementu najwyższego poziomu w obszarze RST, jeśli są one obecne w `SecondaryParameters` elementu. Dołącza WCF `SecondaryParameters` elementu RST wychodzących, nie mają być modyfikowane.  
  
## <a name="rp-trust-feb-2005-and-sts-trust-13"></a>Zaufanie RP luty 2005 i zaufania STS 1.3  
 WSDL dla planu odzyskiwania zawiera następujące elementy w `RequestSecurityTokenTemplate` sekcji:  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
 Plik konfiguracji klienta zawiera listę parametrów.  
  
 Z pliku konfiguracji klienta WCF nie można rozróżnić parametry usługi i klienta. W związku z tym WCF konwertuje wszystkie parametry do przestrzeni nazw w wersji 1.3 zaufania.  
  
 Uchwyty WCF `KeyType`, `KeySize`, i `TokenType` elementy w następujący sposób:  
  
-   Pobieranie pliku WSDL, utwórz powiązanie i przypisz `KeyType`, `KeySize`, i `TokenType` z parametrów planu odzyskiwania. Następnie zostanie wygenerowany plik konfiguracji klienta.  
  
-   Klienta można teraz zmienić żadnego parametru w pliku konfiguracji.  
  
-   W czasie wykonywania, WCF kopiuje wszystkie parametry określonego do `AdditionalTokenParameters` sekcji pliku konfiguracji klienta, z wyjątkiem `KeyType`, `KeySize` i `TokenType`, ponieważ te parametry są wyjaśnić w pliku konfiguracji Generowanie.  
  
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
  
 Usługi WCF kopiuje wszystkie parametry określony w ramach `SecondaryParameters` sekcji, aby element RST najwyższego poziomu, ale nie konwertuje je do przestrzeni nazw protokołu WS-Trust 2005.
