---
title: 'Instrukcje: Zmiana wartości ustawienia między sesjami aplikacji'
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], changing
- application settings [Windows Forms], between application sessions
ms.assetid: 1a85911f-97b2-476c-930b-83379edd890c
ms.openlocfilehash: 95e613cb280813cd75d887d3cf147d7c897bc2e6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59318904"
---
# <a name="how-to-change-the-value-of-a-setting-between-application-sessions"></a><span data-ttu-id="c8861-102">Instrukcje: Zmiana wartości ustawienia między sesjami aplikacji</span><span class="sxs-lookup"><span data-stu-id="c8861-102">How To: Change the Value of a Setting Between Application Sessions</span></span>
<span data-ttu-id="c8861-103">Czasami możesz chcieć zmiany wartości ustawienia między sesjami aplikacji po aplikacji został skompilowany i wdrożony.</span><span class="sxs-lookup"><span data-stu-id="c8861-103">At times, you might want to change the value of a setting between application sessions after the application has been compiled and deployed.</span></span> <span data-ttu-id="c8861-104">Na przykład możesz chcieć Zmień parametry połączenia, aby wskazać lokalizację prawidłową bazę danych.</span><span class="sxs-lookup"><span data-stu-id="c8861-104">For example, you might want to change a connection string to point to the correct database location.</span></span> <span data-ttu-id="c8861-105">Ponieważ narzędzi czasu projektowania nie są dostępne po aplikacji został skompilowany i wdrożone, należy zmienić wartość ustawienia ręcznie w pliku.</span><span class="sxs-lookup"><span data-stu-id="c8861-105">Since design-time tools are not available after the application has been compiled and deployed, you must change the setting value manually in the file.</span></span>  
  
### <a name="to-change-the-value-of-a-setting-between-application-sessions"></a><span data-ttu-id="c8861-106">Aby zmienić wartość ustawienia między sesjami aplikacji</span><span class="sxs-lookup"><span data-stu-id="c8861-106">To Change the Value of a Setting Between Application Sessions</span></span>  
  
1. <span data-ttu-id="c8861-107">Przy użyciu Microsoft Notepad lub części tekstu lub edytorze XML, otwórz plik Config, skojarzone z aplikacją.</span><span class="sxs-lookup"><span data-stu-id="c8861-107">Using Microsoft Notepad or some other text or XML editor, open the .config file associated with your application.</span></span>  
  
2. <span data-ttu-id="c8861-108">Zlokalizuj wpis dla ustawienia, które chcesz zmienić.</span><span class="sxs-lookup"><span data-stu-id="c8861-108">Locate the entry for the setting you want to change.</span></span> <span data-ttu-id="c8861-109">Powinno to wyglądać podobnie jak w przykładzie przedstawione poniżej.</span><span class="sxs-lookup"><span data-stu-id="c8861-109">It should look similar to the example presented below.</span></span>  
  
    ```xml  
    <setting name="Setting1" serializeAs="String" >  
       <value>My Setting Value</value>  
    </setting>  
    ```  
  
3. <span data-ttu-id="c8861-110">Wpisz nową wartość dla ustawienia, a następnie zapisz plik.</span><span class="sxs-lookup"><span data-stu-id="c8861-110">Type a new value for your setting and save the file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8861-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c8861-111">See also</span></span>

- [<span data-ttu-id="c8861-112">Używanie ustawień aplikacji i ustawień użytkownika</span><span class="sxs-lookup"><span data-stu-id="c8861-112">Using Application Settings and User Settings</span></span>](using-application-settings-and-user-settings.md)
- [<span data-ttu-id="c8861-113">Przegląd ustawień aplikacji</span><span class="sxs-lookup"><span data-stu-id="c8861-113">Application Settings Overview</span></span>](application-settings-overview.md)
