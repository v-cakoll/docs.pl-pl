---
title: Niepowodzenia uwierzytelniania i weryfikacji zabezpieczeń na sekundę
ms.date: 03/30/2017
ms.assetid: 266c3bd3-2ffc-4471-94b7-3675443be1ac
ms.openlocfilehash: e3db8cb20399bdff9b73a428ea2a53909da4eee1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61915775"
---
# <a name="security-validation-and-authentication-failures-per-second"></a>Niepowodzenia uwierzytelniania i weryfikacji zabezpieczeń na sekundę
Nazwa komputera: Niepowodzenia uwierzytelniania na sekundę i weryfikacji zabezpieczeń.  
  
## <a name="description"></a>Opis  
 Ten licznik jest zwiększany, gdy komunikat zostanie odrzucony, ze względu na problem z zabezpieczeniami nie pasuje do żadnego licznika "Zabezpieczenia połączeń nie masz praw". Takie problemy obejmują:  
  
- Nie można odczytać tokenu klienta z komunikatu.  
  
- Token klienta nie powiodło się uwierzytelnianie (na przykład nieprawidłowe hasło).  
  
- Weryfikacja podpisu nie powiodła się (na przykład wiadomości zostały zmodyfikowane).  
  
- Komunikat jest duplikatem z poprzedniej wersji, która może się zdarzyć podczas ataku powtarzania.  
  
- Wystąpił błąd odszyfrowywania.  
  
- Niektóre wymagane elementy (na przykład brak sygnatur czasowych lub zaszyfrowanych danych, blokowanie) brakuje wiadomości.  
  
- Wystąpił błąd podczas uzgadniania TLSNEGO/SPNEGO.  
  
 Ten licznik jest typ licznika wydajności [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), którego wartość jest obliczana przy użyciu następującej formuły:  
  
 (N1-N0)/((D1-D0)/F)
