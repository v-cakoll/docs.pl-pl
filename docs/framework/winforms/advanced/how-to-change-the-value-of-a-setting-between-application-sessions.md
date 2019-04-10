---
title: 'Instrukcje: Zmiana wartości ustawienia między sesjami aplikacji'
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], changing
- application settings [Windows Forms], between application sessions
ms.assetid: 1a85911f-97b2-476c-930b-83379edd890c
ms.openlocfilehash: 95e613cb280813cd75d887d3cf147d7c897bc2e6
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59318904"
---
# <a name="how-to-change-the-value-of-a-setting-between-application-sessions"></a>Instrukcje: Zmiana wartości ustawienia między sesjami aplikacji
Czasami możesz chcieć zmiany wartości ustawienia między sesjami aplikacji po aplikacji został skompilowany i wdrożony. Na przykład możesz chcieć Zmień parametry połączenia, aby wskazać lokalizację prawidłową bazę danych. Ponieważ narzędzi czasu projektowania nie są dostępne po aplikacji został skompilowany i wdrożone, należy zmienić wartość ustawienia ręcznie w pliku.  
  
### <a name="to-change-the-value-of-a-setting-between-application-sessions"></a>Aby zmienić wartość ustawienia między sesjami aplikacji  
  
1. Przy użyciu Microsoft Notepad lub części tekstu lub edytorze XML, otwórz plik Config, skojarzone z aplikacją.  
  
2. Zlokalizuj wpis dla ustawienia, które chcesz zmienić. Powinno to wyglądać podobnie jak w przykładzie przedstawione poniżej.  
  
    ```xml  
    <setting name="Setting1" serializeAs="String" >  
       <value>My Setting Value</value>  
    </setting>  
    ```  
  
3. Wpisz nową wartość dla ustawienia, a następnie zapisz plik.  
  
## <a name="see-also"></a>Zobacz także

- [Używanie ustawień aplikacji i ustawień użytkownika](using-application-settings-and-user-settings.md)
- [Przegląd ustawień aplikacji](application-settings-overview.md)
