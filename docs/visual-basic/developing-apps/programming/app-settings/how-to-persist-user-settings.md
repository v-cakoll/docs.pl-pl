---
title: 'Instrukcje: Utrwalanie ustawień użytkownika'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Settings object [Visual Basic], persisting user settings
- persistence [Visual Basic], persisting user settings [Visual Basic]
- user settings [Visual Basic], persisting
ms.assetid: 0e5e6415-b6e2-4602-9be0-a65fa167d007
ms.openlocfilehash: b1026e400015ff7807144dca8e9ce6d72fe3d18e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74329640"
---
# <a name="how-to-persist-user-settings-in-visual-basic"></a><span data-ttu-id="21c4c-102">Porady: utrwalanie ustawień użytkownika w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="21c4c-102">How to: Persist User Settings in Visual Basic</span></span>

<span data-ttu-id="21c4c-103">Możesz użyć metody, `My.Settings.Save` aby zachować zmiany ustawień użytkownika.</span><span class="sxs-lookup"><span data-stu-id="21c4c-103">You can use the `My.Settings.Save` method to persist changes to the user settings.</span></span>  
  
 <span data-ttu-id="21c4c-104">Zazwyczaj aplikacje są przeznaczone do utrwalania zmian ustawień użytkownika po zamknięciu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="21c4c-104">Typically, applications are designed to persist the changes to the user settings when the application shuts down.</span></span> <span data-ttu-id="21c4c-105">Wynika to z faktu, że zapisywanie ustawień może zająć, w zależności od kilku czynników, kilka sekund.</span><span class="sxs-lookup"><span data-stu-id="21c4c-105">This is because saving the settings can take, depending on several factors, several seconds.</span></span>  
  
 <span data-ttu-id="21c4c-106">Aby uzyskać więcej informacji, zobacz [My. Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span><span class="sxs-lookup"><span data-stu-id="21c4c-106">For more information, see [My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="21c4c-107">Chociaż można zmienić i zapisać wartości ustawień zakresu użytkownika w czasie wykonywania, ustawienia zakresu aplikacji są tylko do odczytu i nie można ich programowo zmienić.</span><span class="sxs-lookup"><span data-stu-id="21c4c-107">Although you can change and save the values of user-scope settings at run time, application-scope settings are read-only and cannot be changed programmatically.</span></span> <span data-ttu-id="21c4c-108">Ustawienia zakresu aplikacji można zmienić podczas tworzenia aplikacji, za pomocą **projektanta projektu**lub edytując plik konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="21c4c-108">You can change application-scope settings when creating the application, through the **Project Designer**, or by editing the application's configuration file.</span></span> <span data-ttu-id="21c4c-109">Aby uzyskać więcej informacji, zobacz [Zarządzanie ustawieniami aplikacji (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="21c4c-109">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="example"></a><span data-ttu-id="21c4c-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="21c4c-110">Example</span></span>  

 <span data-ttu-id="21c4c-111">Ten przykład zmienia wartość ustawienia `LastChanged` użytkownika i zapisuje tę zmianę przez wywołanie `My.Settings.Save` metody.</span><span class="sxs-lookup"><span data-stu-id="21c4c-111">This example changes the value of the `LastChanged` user setting and saves that change by calling the `My.Settings.Save` method.</span></span>  
  
 [!code-vb[VbVbalrMyResources#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#5)]  
  
 <span data-ttu-id="21c4c-112">Aby ten przykład działał, aplikacja musi mieć ustawienie `LastChanged` użytkownika o typie. `Date`</span><span class="sxs-lookup"><span data-stu-id="21c4c-112">For this example to work, your application must have a `LastChanged` user setting, of type `Date`.</span></span> <span data-ttu-id="21c4c-113">Aby uzyskać więcej informacji, zobacz [Zarządzanie ustawieniami aplikacji (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="21c4c-113">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21c4c-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="21c4c-114">See also</span></span>

- [<span data-ttu-id="21c4c-115">My.Settings, obiekt</span><span class="sxs-lookup"><span data-stu-id="21c4c-115">My.Settings Object</span></span>](../../../../visual-basic/language-reference/objects/my-settings-object.md)
- [<span data-ttu-id="21c4c-116">Porady: odczytywanie ustawień aplikacji w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="21c4c-116">How to: Read Application Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)
- [<span data-ttu-id="21c4c-117">Porady: zmienianie ustawień użytkownika w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="21c4c-117">How to: Change User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)
- [<span data-ttu-id="21c4c-118">Porady: tworzenie siatek właściwości dla ustawień użytkownika w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="21c4c-118">How to: Create Property Grids for User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)
- [<span data-ttu-id="21c4c-119">Zarządzanie ustawieniami aplikacji (.NET)</span><span class="sxs-lookup"><span data-stu-id="21c4c-119">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)
