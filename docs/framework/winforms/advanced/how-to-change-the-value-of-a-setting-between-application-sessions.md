---
title: 'Porady: zmiana wartości ustawienia między sesjami aplikacji'
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], changing
- application settings [Windows Forms], between application sessions
ms.assetid: 1a85911f-97b2-476c-930b-83379edd890c
ms.openlocfilehash: 383f72f223fb92170d16a9538c94e67825009abb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33523413"
---
# <a name="how-to-change-the-value-of-a-setting-between-application-sessions"></a><span data-ttu-id="137ac-102">Porady: zmiana wartości ustawienia między sesjami aplikacji</span><span class="sxs-lookup"><span data-stu-id="137ac-102">How To: Change the Value of a Setting Between Application Sessions</span></span>
<span data-ttu-id="137ac-103">W czasie można zmienić wartości ustawienia między sesjami aplikacji po aplikacji została skompilowana i wdrożona.</span><span class="sxs-lookup"><span data-stu-id="137ac-103">At times, you might want to change the value of a setting between application sessions after the application has been compiled and deployed.</span></span> <span data-ttu-id="137ac-104">Na przykład można zmienić parametry połączenia, aby wskazać lokalizację poprawną bazą danych.</span><span class="sxs-lookup"><span data-stu-id="137ac-104">For example, you might want to change a connection string to point to the correct database location.</span></span> <span data-ttu-id="137ac-105">Od czasu projektowania narzędzi nie są dostępne po aplikacji została skompilowana i wdrożona, należy zmienić wartość ustawienia ręcznie w pliku.</span><span class="sxs-lookup"><span data-stu-id="137ac-105">Since design-time tools are not available after the application has been compiled and deployed, you must change the setting value manually in the file.</span></span>  
  
### <a name="to-change-the-value-of-a-setting-between-application-sessions"></a><span data-ttu-id="137ac-106">Aby zmienić wartość ustawienia między sesjami aplikacji</span><span class="sxs-lookup"><span data-stu-id="137ac-106">To Change the Value of a Setting Between Application Sessions</span></span>  
  
1.  <span data-ttu-id="137ac-107">Przy użyciu Microsoft Notepad lub części tekstu lub edytora XML, otwórz plik .config skojarzone z aplikacją.</span><span class="sxs-lookup"><span data-stu-id="137ac-107">Using Microsoft Notepad or some other text or XML editor, open the .config file associated with your application.</span></span>  
  
2.  <span data-ttu-id="137ac-108">Znajdź wpis dla ustawienia, które chcesz zmienić.</span><span class="sxs-lookup"><span data-stu-id="137ac-108">Locate the entry for the setting you want to change.</span></span> <span data-ttu-id="137ac-109">Powinien być podobny do przykład przedstawione poniżej.</span><span class="sxs-lookup"><span data-stu-id="137ac-109">It should look similar to the example presented below.</span></span>  
  
    ```xml  
    <setting name="Setting1" serializeAs="String" >  
       <value>My Setting Value</value>  
    </setting>  
    ```  
  
3.  <span data-ttu-id="137ac-110">Wpisz nową wartość dla ustawienia i Zapisz plik.</span><span class="sxs-lookup"><span data-stu-id="137ac-110">Type a new value for your setting and save the file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="137ac-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="137ac-111">See Also</span></span>  
 [<span data-ttu-id="137ac-112">Używanie ustawień aplikacji i ustawień użytkownika</span><span class="sxs-lookup"><span data-stu-id="137ac-112">Using Application Settings and User Settings</span></span>](../../../../docs/framework/winforms/advanced/using-application-settings-and-user-settings.md)  
 [<span data-ttu-id="137ac-113">Przegląd ustawień aplikacji</span><span class="sxs-lookup"><span data-stu-id="137ac-113">Application Settings Overview</span></span>](../../../../docs/framework/winforms/advanced/application-settings-overview.md)
