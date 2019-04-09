---
title: 'Instrukcje: Zmiana wartości ustawienia między sesjami aplikacji'
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], changing
- application settings [Windows Forms], between application sessions
ms.assetid: 1a85911f-97b2-476c-930b-83379edd890c
ms.openlocfilehash: 03a10e95362b1d49e4929c07ab6193f53898d34f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59142860"
---
# <a name="how-to-change-the-value-of-a-setting-between-application-sessions"></a>Instrukcje: Zmiana wartości ustawienia między sesjami aplikacji
Czasami możesz chcieć zmiany wartości ustawienia między sesjami aplikacji po aplikacji został skompilowany i wdrożony. Na przykład możesz chcieć Zmień parametry połączenia, aby wskazać lokalizację prawidłową bazę danych. Ponieważ narzędzi czasu projektowania nie są dostępne po aplikacji został skompilowany i wdrożone, należy zmienić wartość ustawienia ręcznie w pliku.  
  
### <a name="to-change-the-value-of-a-setting-between-application-sessions"></a>Aby zmienić wartość ustawienia między sesjami aplikacji  
  
1.  Przy użyciu Microsoft Notepad lub części tekstu lub edytorze XML, otwórz plik Config, skojarzone z aplikacją.  
  
2.  Zlokalizuj wpis dla ustawienia, które chcesz zmienić. Powinno to wyglądać podobnie jak w przykładzie przedstawione poniżej.  
  
    ```xml  
    <setting name="Setting1" serializeAs="String" >  
       <value>My Setting Value</value>  
    </setting>  
    ```  
  
3.  Wpisz nową wartość dla ustawienia, a następnie zapisz plik.  
  
## <a name="see-also"></a>Zobacz także

- [Używanie ustawień aplikacji i ustawień użytkownika](using-application-settings-and-user-settings.md)
- [Przegląd ustawień aplikacji](application-settings-overview.md)
