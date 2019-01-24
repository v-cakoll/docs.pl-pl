---
title: 'Instrukcje: Zmiana wartości ustawienia między sesjami aplikacji'
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], changing
- application settings [Windows Forms], between application sessions
ms.assetid: 1a85911f-97b2-476c-930b-83379edd890c
ms.openlocfilehash: 475e57e8bfdd5f3296c6af0fb20a472c729ea75c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54540718"
---
# <a name="how-to-change-the-value-of-a-setting-between-application-sessions"></a><span data-ttu-id="2c65f-102">Instrukcje: Zmiana wartości ustawienia między sesjami aplikacji</span><span class="sxs-lookup"><span data-stu-id="2c65f-102">How To: Change the Value of a Setting Between Application Sessions</span></span>
<span data-ttu-id="2c65f-103">Czasami możesz chcieć zmiany wartości ustawienia między sesjami aplikacji po aplikacji został skompilowany i wdrożony.</span><span class="sxs-lookup"><span data-stu-id="2c65f-103">At times, you might want to change the value of a setting between application sessions after the application has been compiled and deployed.</span></span> <span data-ttu-id="2c65f-104">Na przykład możesz chcieć Zmień parametry połączenia, aby wskazać lokalizację prawidłową bazę danych.</span><span class="sxs-lookup"><span data-stu-id="2c65f-104">For example, you might want to change a connection string to point to the correct database location.</span></span> <span data-ttu-id="2c65f-105">Ponieważ narzędzi czasu projektowania nie są dostępne po aplikacji został skompilowany i wdrożone, należy zmienić wartość ustawienia ręcznie w pliku.</span><span class="sxs-lookup"><span data-stu-id="2c65f-105">Since design-time tools are not available after the application has been compiled and deployed, you must change the setting value manually in the file.</span></span>  
  
### <a name="to-change-the-value-of-a-setting-between-application-sessions"></a><span data-ttu-id="2c65f-106">Aby zmienić wartość ustawienia między sesjami aplikacji</span><span class="sxs-lookup"><span data-stu-id="2c65f-106">To Change the Value of a Setting Between Application Sessions</span></span>  
  
1.  <span data-ttu-id="2c65f-107">Przy użyciu Microsoft Notepad lub części tekstu lub edytorze XML, otwórz plik Config, skojarzone z aplikacją.</span><span class="sxs-lookup"><span data-stu-id="2c65f-107">Using Microsoft Notepad or some other text or XML editor, open the .config file associated with your application.</span></span>  
  
2.  <span data-ttu-id="2c65f-108">Zlokalizuj wpis dla ustawienia, które chcesz zmienić.</span><span class="sxs-lookup"><span data-stu-id="2c65f-108">Locate the entry for the setting you want to change.</span></span> <span data-ttu-id="2c65f-109">Powinno to wyglądać podobnie jak w przykładzie przedstawione poniżej.</span><span class="sxs-lookup"><span data-stu-id="2c65f-109">It should look similar to the example presented below.</span></span>  
  
    ```xml  
    <setting name="Setting1" serializeAs="String" >  
       <value>My Setting Value</value>  
    </setting>  
    ```  
  
3.  <span data-ttu-id="2c65f-110">Wpisz nową wartość dla ustawienia, a następnie zapisz plik.</span><span class="sxs-lookup"><span data-stu-id="2c65f-110">Type a new value for your setting and save the file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c65f-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2c65f-111">See also</span></span>
- [<span data-ttu-id="2c65f-112">Używanie ustawień aplikacji i ustawień użytkownika</span><span class="sxs-lookup"><span data-stu-id="2c65f-112">Using Application Settings and User Settings</span></span>](../../../../docs/framework/winforms/advanced/using-application-settings-and-user-settings.md)
- [<span data-ttu-id="2c65f-113">Przegląd ustawień aplikacji</span><span class="sxs-lookup"><span data-stu-id="2c65f-113">Application Settings Overview</span></span>](../../../../docs/framework/winforms/advanced/application-settings-overview.md)
