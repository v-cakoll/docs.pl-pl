---
title: 'Punkt końcowy: Błędy walidacji zabezpieczeń i uwierzytelniania'
ms.date: 03/30/2017
ms.assetid: 5bad60aa-6084-4c7b-aefd-9b581f04382e
author: BrucePerlerMS
ms.openlocfilehash: f7cd2268eefa0176ab71a3d5d3bc82c178664742
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2018
ms.locfileid: "48837863"
---
# <a name="endpoint-security-validation-and-authentication-failures"></a>Punkt końcowy: Błędy walidacji zabezpieczeń i uwierzytelniania
Nazwa licznika: błędy walidacji zabezpieczeń i uwierzytelniania  
  
## <a name="description"></a>Opis  
 Ten licznik jest zwiększany, gdy komunikat zostanie odrzucony, ze względu na problem z zabezpieczeniami nie pasuje do żadnego licznika "Zabezpieczenia połączeń nie masz praw". Takie problemy obejmują:  
  
-   Nie można odczytać tokenu klienta z komunikatu.  
  
-   Token klienta nie powiodło się uwierzytelnianie (nieprawidłowe hasło).  
  
-   Weryfikacja podpisu nie powiodła się (komunikat został zmodyfikowany).  
  
-   Komunikat jest duplikatem z poprzedniej wersji, która może się zdarzyć podczas ataku powtarzania.  
  
-   Wystąpił błąd odszyfrowywania.  
  
-   Komunikat brakuje niektórych wymaganych elementów (Brak znacznika czasu lub zaszyfrowanego bloku danych).  
  
-   Wystąpił błąd podczas uzgadniania TLSNEGO/SPNEGO.
