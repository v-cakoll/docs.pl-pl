---
title: 'Usługa: Błędy walidacji i uwierzytelniania'
ms.date: 03/30/2017
ms.assetid: 55c98268-b1ad-459d-851b-25ef52248187
ms.openlocfilehash: 399249926bcb1383fd33f60510c2c212c6f4261c
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/20/2019
ms.locfileid: "74204582"
---
# <a name="service-security-validation-and-authentication-failures"></a>Usługa: Błędy walidacji i uwierzytelniania
Nazwa licznika: Błędy walidacji zabezpieczeń i uwierzytelniania  
  
## <a name="description"></a>Opis  
 Ten licznik jest zwiększany za każdym razem, gdy komunikat zostanie odrzucony z powodu problemu z zabezpieczeniami, którego nie dotyczy licznik "wywołania zabezpieczeń bez autoryzacji". Takie problemy obejmują:  
  
- Nie można odczytać z komunikatu tokenu klienta.  
  
- Uwierzytelnianie tokenu klienta nie powiodło się (na przykład złe hasło).  
  
- Weryfikacja podpisu nie powiodła się (na przykład komunikat został naruszony).  
  
- Komunikat jest duplikatem z poprzedniego, który może wystąpić podczas ataku metodą powtórzeń.  
  
- Wystąpił błąd odszyfrowywania.  
  
- W komunikacie brakuje niektórych wymaganych elementów (na przykład braku sygnatury czasowej lub zaszyfrowanego bloku danych).  
  
- Wystąpiły błędy podczas uzgadniania TLSNEGO/SPNEGO.
