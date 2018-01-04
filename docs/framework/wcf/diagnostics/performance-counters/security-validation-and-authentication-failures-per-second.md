---
title: "Niepowodzenia uwierzytelniania i walidacji zabezpieczeń na sekundę"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 266c3bd3-2ffc-4471-94b7-3675443be1ac
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 8159527f8f958c747a464641c69910c9df1b3d4e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="security-validation-and-authentication-failures-per-second"></a>Niepowodzenia uwierzytelniania i walidacji zabezpieczeń na sekundę
Nazwa licznika: walidacji i uwierzytelniania błędów na sekundę.  
  
## <a name="description"></a>Opis  
 Ten licznik jest zwiększany, gdy komunikat jest odrzucone z powodu problemu zabezpieczeń nie pasuje do żadnego licznika "Zabezpieczeń wywołań nieautoryzowane". Takie problemy obejmują:  
  
-   Nie można odczytać tokenu klienta z komunikatu.  
  
-   Token klienta nie powiodło się uwierzytelniania (na przykład nieprawidłowe hasło).  
  
-   Weryfikacja podpisu nie powiodła się (na przykład wiadomości została naruszona).  
  
-   Komunikat jest duplikatem z poprzedniej wersji, która może się zdarzyć podczas atakiem polegającym na odtwarzaniu.  
  
-   Wystąpił błąd odszyfrowywania.  
  
-   Niektóre elementy (na przykład brak sygnatury czasowej lub zaszyfrowanych danych, blokowanie) brakuje wymaganych z komunikatu.  
  
-   Wystąpił błąd podczas uzgadniania TLSNEGO/SPNEGO.  
  
 Ten licznik jest typu licznika wydajności [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), którego wartość jest obliczana przy użyciu następującej formuły:  
  
 (N1-N0)/((D1-D0)/F)
