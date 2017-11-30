---
title: "Porady: zmiana wartości ustawienia między sesjami aplikacji"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application settings [Windows Forms], changing
- application settings [Windows Forms], between application sessions
ms.assetid: 1a85911f-97b2-476c-930b-83379edd890c
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2dff90e499ce421f372137903daf34c09c21d5c7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-change-the-value-of-a-setting-between-application-sessions"></a>Porady: zmiana wartości ustawienia między sesjami aplikacji
W czasie można zmienić wartości ustawienia między sesjami aplikacji po aplikacji została skompilowana i wdrożona. Na przykład można zmienić parametry połączenia, aby wskazać lokalizację poprawną bazą danych. Od czasu projektowania narzędzi nie są dostępne po aplikacji została skompilowana i wdrożona, należy zmienić wartość ustawienia ręcznie w pliku.  
  
### <a name="to-change-the-value-of-a-setting-between-application-sessions"></a>Aby zmienić wartość ustawienia między sesjami aplikacji  
  
1.  Przy użyciu Microsoft Notepad lub części tekstu lub edytora XML, otwórz plik .config skojarzone z aplikacją.  
  
2.  Znajdź wpis dla ustawienia, które chcesz zmienić. Powinien być podobny do przykład przedstawione poniżej.  
  
    ```xml  
    <setting name="Setting1" serializeAs="String" >  
       <value>My Setting Value</value>  
    </setting>  
    ```  
  
3.  Wpisz nową wartość dla ustawienia i Zapisz plik.  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie ustawień aplikacji i ustawień użytkownika](../../../../docs/framework/winforms/advanced/using-application-settings-and-user-settings.md)  
 [Przegląd ustawień aplikacji](../../../../docs/framework/winforms/advanced/application-settings-overview.md)
