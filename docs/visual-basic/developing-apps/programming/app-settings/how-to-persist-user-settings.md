---
title: 'Instrukcje: Utrwalanie ustawień użytkownika w Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Settings object [Visual Basic], persisting user settings
- persistence [Visual Basic], persisting user settings [Visual Basic]
- user settings [Visual Basic], persisting
ms.assetid: 0e5e6415-b6e2-4602-9be0-a65fa167d007
ms.openlocfilehash: 0683a5c359da1c4d082f7312c1ed8f43e1c151f3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968376"
---
# <a name="how-to-persist-user-settings-in-visual-basic"></a><span data-ttu-id="06b21-102">Instrukcje: Utrwalanie ustawień użytkownika w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="06b21-102">How to: Persist User Settings in Visual Basic</span></span>
<span data-ttu-id="06b21-103">Możesz użyć metody, `My.Settings.Save` aby zachować zmiany ustawień użytkownika.</span><span class="sxs-lookup"><span data-stu-id="06b21-103">You can use the `My.Settings.Save` method to persist changes to the user settings.</span></span>  
  
 <span data-ttu-id="06b21-104">Zazwyczaj aplikacje są przeznaczone do utrwalania zmian ustawień użytkownika po zamknięciu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="06b21-104">Typically, applications are designed to persist the changes to the user settings when the application shuts down.</span></span> <span data-ttu-id="06b21-105">Wynika to z faktu, że zapisywanie ustawień może zająć, w zależności od kilku czynników, kilka sekund.</span><span class="sxs-lookup"><span data-stu-id="06b21-105">This is because saving the settings can take, depending on several factors, several seconds.</span></span>  
  
 <span data-ttu-id="06b21-106">Aby uzyskać więcej informacji, zobacz [My. Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span><span class="sxs-lookup"><span data-stu-id="06b21-106">For more information, see [My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="06b21-107">Chociaż można zmienić i zapisać wartości ustawień zakresu użytkownika w czasie wykonywania, ustawienia zakresu aplikacji są tylko do odczytu i nie można ich programowo zmienić.</span><span class="sxs-lookup"><span data-stu-id="06b21-107">Although you can change and save the values of user-scope settings at run time, application-scope settings are read-only and cannot be changed programmatically.</span></span> <span data-ttu-id="06b21-108">Ustawienia zakresu aplikacji można zmienić podczas tworzenia aplikacji, za pomocą **projektanta projektu**lub edytując plik konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="06b21-108">You can change application-scope settings when creating the application, through the **Project Designer**, or by editing the application's configuration file.</span></span> <span data-ttu-id="06b21-109">Aby uzyskać więcej informacji, zobacz [Zarządzanie ustawieniami aplikacji (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="06b21-109">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="example"></a><span data-ttu-id="06b21-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="06b21-110">Example</span></span>  
 <span data-ttu-id="06b21-111">Ten przykład zmienia wartość `LastChanged` ustawienia użytkownika i zapisuje tę zmianę przez `My.Settings.Save` wywołanie metody.</span><span class="sxs-lookup"><span data-stu-id="06b21-111">This example changes the value of the `LastChanged` user setting and saves that change by calling the `My.Settings.Save` method.</span></span>  
  
 [!code-vb[VbVbalrMyResources#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#5)]  
  
 <span data-ttu-id="06b21-112">Aby ten przykład działał, aplikacja musi mieć `LastChanged` ustawienie użytkownika o typie. `Date`</span><span class="sxs-lookup"><span data-stu-id="06b21-112">For this example to work, your application must have a `LastChanged` user setting, of type `Date`.</span></span> <span data-ttu-id="06b21-113">Aby uzyskać więcej informacji, zobacz [Zarządzanie ustawieniami aplikacji (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="06b21-113">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06b21-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="06b21-114">See also</span></span>

- [<span data-ttu-id="06b21-115">My.Settings, obiekt</span><span class="sxs-lookup"><span data-stu-id="06b21-115">My.Settings Object</span></span>](../../../../visual-basic/language-reference/objects/my-settings-object.md)
- [<span data-ttu-id="06b21-116">Instrukcje: Odczytaj ustawienia aplikacji w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="06b21-116">How to: Read Application Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)
- [<span data-ttu-id="06b21-117">Instrukcje: Zmień ustawienia użytkownika w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="06b21-117">How to: Change User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)
- [<span data-ttu-id="06b21-118">Instrukcje: Tworzenie siatek właściwości dla ustawień użytkownika w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="06b21-118">How to: Create Property Grids for User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)
- [<span data-ttu-id="06b21-119">Zarządzanie ustawieniami aplikacji (.NET)</span><span class="sxs-lookup"><span data-stu-id="06b21-119">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)
