---
title: Błędy walidacji zabezpieczeń i uwierzytelniania
ms.date: 03/30/2017
ms.assetid: 0d4e3666-dfc6-421c-baf8-9479c22f7050
ms.openlocfilehash: 32a7d41f93dd99f1950a073e1cac1b62177ff6c3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61916048"
---
# <a name="security-validation-and-authentication-failures"></a>Błędy walidacji zabezpieczeń i uwierzytelniania
Nazwa komputera: Błędy walidacji zabezpieczeń i uwierzytelniania  
  
## <a name="description"></a>Opis  
 Ten licznik jest zwiększany, gdy komunikat zostanie odrzucony, ze względu na problem z zabezpieczeniami nie pasuje do żadnego licznika "Zabezpieczenia połączeń nie masz praw". Takie problemy obejmują:  
  
- Nie można odczytać tokenu klienta z komunikatu.  
  
- Token klienta nie powiodło się uwierzytelnianie (na przykład nieprawidłowe hasło).  
  
- Weryfikacja podpisu nie powiodła się (na przykład wiadomości zostały zmodyfikowane).  
  
- Komunikat jest duplikatem z poprzedniej wersji, która może się zdarzyć podczas ataku powtarzania.  
  
- Wystąpił błąd odszyfrowywania.  
  
- Niektóre wymagane elementy (na przykład brak sygnatur czasowych lub zaszyfrowanych danych, blokowanie) brakuje wiadomości.  
  
- Wystąpił błąd podczas uzgadniania TLSNEGO/SPNEGO.
