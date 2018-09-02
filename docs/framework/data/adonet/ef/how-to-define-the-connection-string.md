---
title: 'Porady: Określanie parametrów połączenia'
ms.date: 03/30/2017
ms.assetid: 6027335d-4e26-420d-9151-6523289b1989
ms.openlocfilehash: f40b8bc68eda1cb4b64b34d12b2922da69929203
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43387757"
---
# <a name="how-to-define-the-connection-string"></a>Porady: Określanie parametrów połączenia
W tym temacie pokazano, jak zdefiniować parametry połączenia, który jest używany podczas nawiązywania połączenia z modelu koncepcyjnego. Ten temat opiera się na [sprzedaży AdventureWorks](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) modelu koncepcyjnego. W całym tematy związane z zadaniem używany jest Model sprzedaż AdventureWorks [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] dokumentacji. W tym temacie założono, że użytkownik skonfigurował już [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] i zdefiniowane AdventureWorks Sales Model. Aby uzyskać więcej informacji, zobacz [jak: ręcznie zdefiniować modelu i mapowania plików](https://msdn.microsoft.com/library/d4fd6864-f2a1-48f0-aa32-1e318775a99a). Procedury przedstawione w tym temacie znajdują się również w [porady: ręczne skonfigurowanie projektu programu Entity Framework](https://msdn.microsoft.com/library/73f6ae1d-b3b2-4577-aebd-ad5a75954e9e).  
  
> [!NOTE]
>  Jeśli używasz [!INCLUDE[adonet_edm](../../../../../includes/adonet-edm-md.md)] kreatora w projekcie programu Visual Studio automatycznie generuje plik edmx i konfiguruje projekt, aby użyć [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. Aby uzyskać więcej informacji, zobacz [porady: Użyj Kreator modelu Entity Data Model](https://msdn.microsoft.com/library/dadb058a-c5d9-4c5c-8b01-28044112231d)  
  
### <a name="to-define-the-entity-framework-connection-string"></a>Aby zdefiniować parametry połączenia programu Entity Framework  
  
-   Otwórz plik konfiguracji aplikacji projektu (app.config) i dodaj następujące parametry połączenia:  
  
  
  
     Jeśli projekt nie ma pliku konfiguracji aplikacji, możesz dodać kategorię, wybierając **Dodaj nowy element** z **projektu** menu, wybierając **ogólne** kategorii Wybieranie **pliku konfiguracji aplikacji**, a następnie klikając polecenie **Dodaj**.  
  
## <a name="see-also"></a>Zobacz też  
 [Szybki start](https://msdn.microsoft.com/library/0bc534be-789f-4819-b9f6-76e51d961675)  
 [Porady: Tworzenie nowego pliku edmx](https://msdn.microsoft.com/library/beb8189e-e51c-4051-839c-9902c224abf2)  
 [Narzędzia do modelu danych jednostki ADO.NET](https://msdn.microsoft.com/library/91076853-0881-421b-837a-f582f36be527)
