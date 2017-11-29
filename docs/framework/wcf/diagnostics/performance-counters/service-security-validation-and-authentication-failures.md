---
title: "Usługa: Błędy walidacji i uwierzytelniania"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 55c98268-b1ad-459d-851b-25ef52248187
caps.latest.revision: "7"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 808c0d648043df6c5a3dda4646e45ba1492345a0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="service-security-validation-and-authentication-failures"></a>Usługa: Błędy walidacji i uwierzytelniania
Nazwa licznika: błędy walidacji zabezpieczeń i uwierzytelniania  
  
## <a name="description"></a>Opis  
 Ten licznik jest zwiększany, gdy komunikat jest odrzucone z powodu problemu zabezpieczeń nie pasuje do żadnego licznika "Zabezpieczeń wywołań nieautoryzowane". Takie problemy obejmują:  
  
-   Nie można odczytać tokenu klienta z komunikatu.  
  
-   Token klienta nie powiodło się uwierzytelniania (na przykład,, nieprawidłowe hasło).  
  
-   Weryfikacja podpisu nie powiodła się (na przykład, że wiadomość została naruszona).  
  
-   Komunikat jest duplikatem z poprzedniej wersji, która może się zdarzyć podczas atakiem polegającym na odtwarzaniu.  
  
-   Wystąpił błąd odszyfrowywania.  
  
-   Niektóre elementy (na przykład, brak sygnatury czasowej lub zaszyfrowanych danych, blokowanie) brakuje wymaganych z komunikatu.  
  
-   Wystąpił błąd podczas uzgadniania TLSNEGO/SPNEGO.
