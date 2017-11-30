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
# <a name="how-to-change-the-value-of-a-setting-between-application-sessions"></a><span data-ttu-id="f1fac-102">Porady: zmiana wartości ustawienia między sesjami aplikacji</span><span class="sxs-lookup"><span data-stu-id="f1fac-102">How To: Change the Value of a Setting Between Application Sessions</span></span>
<span data-ttu-id="f1fac-103">W czasie można zmienić wartości ustawienia między sesjami aplikacji po aplikacji została skompilowana i wdrożona.</span><span class="sxs-lookup"><span data-stu-id="f1fac-103">At times, you might want to change the value of a setting between application sessions after the application has been compiled and deployed.</span></span> <span data-ttu-id="f1fac-104">Na przykład można zmienić parametry połączenia, aby wskazać lokalizację poprawną bazą danych.</span><span class="sxs-lookup"><span data-stu-id="f1fac-104">For example, you might want to change a connection string to point to the correct database location.</span></span> <span data-ttu-id="f1fac-105">Od czasu projektowania narzędzi nie są dostępne po aplikacji została skompilowana i wdrożona, należy zmienić wartość ustawienia ręcznie w pliku.</span><span class="sxs-lookup"><span data-stu-id="f1fac-105">Since design-time tools are not available after the application has been compiled and deployed, you must change the setting value manually in the file.</span></span>  
  
### <a name="to-change-the-value-of-a-setting-between-application-sessions"></a><span data-ttu-id="f1fac-106">Aby zmienić wartość ustawienia między sesjami aplikacji</span><span class="sxs-lookup"><span data-stu-id="f1fac-106">To Change the Value of a Setting Between Application Sessions</span></span>  
  
1.  <span data-ttu-id="f1fac-107">Przy użyciu Microsoft Notepad lub części tekstu lub edytora XML, otwórz plik .config skojarzone z aplikacją.</span><span class="sxs-lookup"><span data-stu-id="f1fac-107">Using Microsoft Notepad or some other text or XML editor, open the .config file associated with your application.</span></span>  
  
2.  <span data-ttu-id="f1fac-108">Znajdź wpis dla ustawienia, które chcesz zmienić.</span><span class="sxs-lookup"><span data-stu-id="f1fac-108">Locate the entry for the setting you want to change.</span></span> <span data-ttu-id="f1fac-109">Powinien być podobny do przykład przedstawione poniżej.</span><span class="sxs-lookup"><span data-stu-id="f1fac-109">It should look similar to the example presented below.</span></span>  
  
    ```xml  
    <setting name="Setting1" serializeAs="String" >  
       <value>My Setting Value</value>  
    </setting>  
    ```  
  
3.  <span data-ttu-id="f1fac-110">Wpisz nową wartość dla ustawienia i Zapisz plik.</span><span class="sxs-lookup"><span data-stu-id="f1fac-110">Type a new value for your setting and save the file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1fac-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f1fac-111">See Also</span></span>  
 [<span data-ttu-id="f1fac-112">Używanie ustawień aplikacji i ustawień użytkownika</span><span class="sxs-lookup"><span data-stu-id="f1fac-112">Using Application Settings and User Settings</span></span>](../../../../docs/framework/winforms/advanced/using-application-settings-and-user-settings.md)  
 [<span data-ttu-id="f1fac-113">Przegląd ustawień aplikacji</span><span class="sxs-lookup"><span data-stu-id="f1fac-113">Application Settings Overview</span></span>](../../../../docs/framework/winforms/advanced/application-settings-overview.md)
