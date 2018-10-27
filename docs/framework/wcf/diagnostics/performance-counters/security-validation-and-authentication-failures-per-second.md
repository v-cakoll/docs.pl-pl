---
title: Niepowodzenia uwierzytelniania i walidacji zabezpieczeń na sekundę
ms.date: 03/30/2017
ms.assetid: 266c3bd3-2ffc-4471-94b7-3675443be1ac
ms.openlocfilehash: e3db8cb20399bdff9b73a428ea2a53909da4eee1
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50088770"
---
# <a name="security-validation-and-authentication-failures-per-second"></a>Niepowodzenia uwierzytelniania i walidacji zabezpieczeń na sekundę
Nazwa licznika: walidacji zabezpieczeń i uwierzytelniania błędy na sekundę.  
  
## <a name="description"></a>Opis  
 Ten licznik jest zwiększany, gdy komunikat zostanie odrzucony, ze względu na problem z zabezpieczeniami nie pasuje do żadnego licznika "Zabezpieczenia połączeń nie masz praw". Takie problemy obejmują:  
  
-   Nie można odczytać tokenu klienta z komunikatu.  
  
-   Token klienta nie powiodło się uwierzytelnianie (na przykład nieprawidłowe hasło).  
  
-   Weryfikacja podpisu nie powiodła się (na przykład wiadomości zostały zmodyfikowane).  
  
-   Komunikat jest duplikatem z poprzedniej wersji, która może się zdarzyć podczas ataku powtarzania.  
  
-   Wystąpił błąd odszyfrowywania.  
  
-   Niektóre wymagane elementy (na przykład brak sygnatur czasowych lub zaszyfrowanych danych, blokowanie) brakuje wiadomości.  
  
-   Wystąpił błąd podczas uzgadniania TLSNEGO/SPNEGO.  
  
 Ten licznik jest typ licznika wydajności [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), którego wartość jest obliczana przy użyciu następującej formuły:  
  
 (N1-N0)/((D1-D0)/F)
