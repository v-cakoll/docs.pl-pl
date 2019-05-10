---
title: 'Punkt końcowy: Błędy walidacji zabezpieczeń i uwierzytelniania'
ms.date: 03/30/2017
ms.assetid: 5bad60aa-6084-4c7b-aefd-9b581f04382e
ms.openlocfilehash: 9e0192ea600bb52abd555f2f83cfe8e96d3fe203
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64619337"
---
# <a name="endpoint-security-validation-and-authentication-failures"></a>Punkt końcowy: Błędy walidacji zabezpieczeń i uwierzytelniania
Nazwa komputera: Błędy walidacji zabezpieczeń i uwierzytelniania  
  
## <a name="description"></a>Opis  
 Ten licznik jest zwiększany, gdy komunikat zostanie odrzucony, ze względu na problem z zabezpieczeniami nie pasuje do żadnego licznika "Zabezpieczenia połączeń nie masz praw". Takie problemy obejmują:  
  
- Nie można odczytać tokenu klienta z komunikatu.  
  
- Token klienta nie powiodło się uwierzytelnianie (nieprawidłowe hasło).  
  
- Weryfikacja podpisu nie powiodła się (komunikat został zmodyfikowany).  
  
- Komunikat jest duplikatem z poprzedniej wersji, która może się zdarzyć podczas ataku powtarzania.  
  
- Wystąpił błąd odszyfrowywania.  
  
- Komunikat brakuje niektórych wymaganych elementów (Brak znacznika czasu lub zaszyfrowanego bloku danych).  
  
- Wystąpił błąd podczas uzgadniania TLSNEGO/SPNEGO.
