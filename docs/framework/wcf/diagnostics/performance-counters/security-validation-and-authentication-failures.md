---
title: "Błędy walidacji zabezpieczeń i uwierzytelniania"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0d4e3666-dfc6-421c-baf8-9479c22f7050
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: c1d448d709c7ad20e9d08a291f5a38546cd93ce4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="security-validation-and-authentication-failures"></a>Błędy walidacji zabezpieczeń i uwierzytelniania
Nazwa licznika: błędy walidacji zabezpieczeń i uwierzytelniania  
  
## <a name="description"></a>Opis  
 Ten licznik jest zwiększany, gdy komunikat jest odrzucone z powodu problemu zabezpieczeń nie pasuje do żadnego licznika "Zabezpieczeń wywołań nieautoryzowane". Takie problemy obejmują:  
  
-   Nie można odczytać tokenu klienta z komunikatu.  
  
-   Token klienta nie powiodło się uwierzytelniania (na przykład nieprawidłowe hasło).  
  
-   Weryfikacja podpisu nie powiodła się (na przykład wiadomości została naruszona).  
  
-   Komunikat jest duplikatem z poprzedniej wersji, która może się zdarzyć podczas atakiem polegającym na odtwarzaniu.  
  
-   Wystąpił błąd odszyfrowywania.  
  
-   Niektóre elementy (na przykład brak sygnatury czasowej lub zaszyfrowanych danych, blokowanie) brakuje wymaganych z komunikatu.  
  
-   Wystąpił błąd podczas uzgadniania TLSNEGO/SPNEGO.
