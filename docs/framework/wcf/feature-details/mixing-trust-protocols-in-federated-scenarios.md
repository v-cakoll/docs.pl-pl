---
title: Mieszanie protokołów zaufania w scenariuszach obejmujących federację
ms.date: 03/30/2017
ms.assetid: d7b5fee9-2246-4b09-b8d7-9e63cb817279
author: BrucePerlerMS
ms.openlocfilehash: d4290880d8d708811a95b38356aa61f0d23c89a8
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/02/2018
ms.locfileid: "48030080"
---
# <a name="mixing-trust-protocols-in-federated-scenarios"></a>Mieszanie protokołów zaufania w scenariuszach obejmujących federację
Mogą istnieć scenariusze, w których federacyjnego klienci komunikują się z usługą i Usługa tokenu zabezpieczającego (STS), które nie mają tę samą wersję zaufania. Usługa może zawierać WSDL `RequestSecurityTokenTemplate` potwierdzenia z elementami WS-Trust, które są w różnych wersjach niż usługi STS. W takich przypadkach klienta usługi Windows Communication Foundation (WCF) konwertuje elementy WS-Trust otrzymane od `RequestSecurityTokenTemplate` do dopasowania usługi STS zaufania wersji. Usługi WCF obsługuje wersje niedopasowanych zaufania tylko standardowe powiązania. Wszystkie parametry algorytmu standard, które są rozpoznawane przez architekturę WCF są częścią standardowych powiązania. W tym temacie opisano zachowanie WCF za pomocą różnych ustawień zaufania między usługą i Usługa tokenu Zabezpieczającego.  
  
## <a name="rp-feb-2005-and-sts-feb-2005"></a>Jednostki Uzależnionej lut 2005 i STS lut 2005  
 WSDL dla jednostki uzależnionej strona (RP) zawiera następujące elementy w ramach `RequestSecurityTokenTemplate` sekcji:  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
 Plik konfiguracji klienta zawiera listę parametrów.  
  
 Usługi WCF nie rozróżnienia między klientem a usługą parametrów; dodaje wszystkie parametry i wysyła je w `RequestSecurityTokenTemplate` (RST).  
  
## <a name="rp-trust-13-and-sts-trust-13"></a>Zaufania jednostki Uzależnionej 1.3 i usługi STS Trust 1.3  
 WSDL dla jednostki Uzależnionej zawiera następujące elementy w ramach `RequestSecurityTokenTemplate` sekcji:  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
-   `KeyWrapAlgorithm`  
  
 Plik konfiguracji klienta zawiera `secondaryParameters` element, który otacza parametrów określonych przez jednostkę Uzależnioną.  
  
 Usuwa WCF `EncryptionAlgorithm`, `CanonicalizationAlgorithm` i `KeyWrapAlgorithm` elementy z element najwyższego poziomu w ramach RST, jeśli są obecne w `SecondaryParameters` elementu. Dołącza WCF `SecondaryParameters` elementu wychodzących RST, bez modyfikacji.  
  
## <a name="rp-trust-feb-2005-and-sts-trust-13"></a>Zaufania jednostki Uzależnionej lut 2005 i STS Trust 1.3  
 WSDL dla jednostki Uzależnionej zawiera następujące elementy w `RequestSecurityTokenTemplate` sekcji:  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
 Plik konfiguracji klienta zawiera listę parametrów.  
  
 Z pliku konfiguracji klienta WCF nie można odróżnić parametry usługi i klienta. W związku z tym WCF konwertuje wszystkie parametry do przestrzeni nazw w wersji 1.3 zaufania.  
  
 Uchwyty WCF `KeyType`, `KeySize`, i `TokenType` elementy w następujący sposób:  
  
-   Pobieranie pliku WSDL, utworzyć powiązanie i przypisać `KeyType`, `KeySize`, i `TokenType` z parametrów jednostki Uzależnionej. Następnie zostanie wygenerowany plik konfiguracji klienta.  
  
-   Klienta można teraz zmienić żadnych parametrów w pliku konfiguracji.  
  
-   Podczas wykonywania programu WCF kopiuje wszystkie parametry określoną `AdditionalTokenParameters` sekcji w pliku konfiguracji klienta, z wyjątkiem `KeyType`, `KeySize` i `TokenType`, ponieważ te parametry są rozliczane w pliku konfiguracji Generowanie.  
  
## <a name="rp-trust-13-and-sts-trust-feb-2005"></a>Zaufania jednostki Uzależnionej 1.3 i zaufanie usługi STS lut 2005  
 WSDL dla jednostki Uzależnionej zawiera następujące elementy w `RequestSecurityTokenTemplate` sekcji:  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
-   `KeyWrapAlgorithm`  
  
 Plik konfiguracji klienta zawiera `secondaryParamters` element, który otacza parametrów określonych przez jednostkę Uzależnioną.  
  
 Usługi WCF kopiuje wszystkie parametry, które są określone w `SecondaryParameters` sekcji, aby element najwyższego poziomu RST, ale nie konwertuje je do przestrzeni nazw protokołu WS-Trust 2005.
