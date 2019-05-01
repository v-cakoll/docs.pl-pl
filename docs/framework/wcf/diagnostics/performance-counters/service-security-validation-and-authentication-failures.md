---
title: 'Usługa: Błędy walidacji zabezpieczeń i uwierzytelniania'
ms.date: 03/30/2017
ms.assetid: 55c98268-b1ad-459d-851b-25ef52248187
ms.openlocfilehash: ba8da3ae6be6bd089690359f19e153da1e0b54fc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61998312"
---
# <a name="service-security-validation-and-authentication-failures"></a>Usługa: Błędy walidacji zabezpieczeń i uwierzytelniania
Nazwa komputera: Błędy walidacji zabezpieczeń i uwierzytelniania  
  
## <a name="description"></a>Opis  
 Ten licznik jest zwiększany, gdy komunikat zostanie odrzucony, ze względu na problem z zabezpieczeniami nie pasuje do żadnego licznika "Zabezpieczenia połączeń nie masz praw". Takie problemy obejmują:  
  
- Nie można odczytać tokenu klienta z komunikatu.  
  
- Token klienta nie powiodło się uwierzytelnianie (na przykład,, nieprawidłowe hasło).  
  
- Weryfikacja podpisu nie powiodła się (na przykład,, wiadomości zostały zmodyfikowane).  
  
- Komunikat jest duplikatem z poprzedniej wersji, która może się zdarzyć podczas ataku powtarzania.  
  
- Wystąpił błąd odszyfrowywania.  
  
- Niektóre wymagane elementy (na przykład,, brak sygnatur czasowych lub zaszyfrowanych danych, blokowanie) brakuje wiadomości.  
  
- Wystąpił błąd podczas uzgadniania TLSNEGO/SPNEGO.
