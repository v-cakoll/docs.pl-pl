---
title: 'Instrukcje: utrwalanie ustawień użytkownika'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Settings object [Visual Basic], persisting user settings
- persistence [Visual Basic], persisting user settings [Visual Basic]
- user settings [Visual Basic], persisting
ms.assetid: 0e5e6415-b6e2-4602-9be0-a65fa167d007
ms.openlocfilehash: b1026e400015ff7807144dca8e9ce6d72fe3d18e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74329640"
---
# <a name="how-to-persist-user-settings-in-visual-basic"></a><span data-ttu-id="e3cd2-102">Porady: utrwalanie ustawień użytkownika w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e3cd2-102">How to: Persist User Settings in Visual Basic</span></span>

<span data-ttu-id="e3cd2-103">Możesz użyć metody `My.Settings.Save`, aby zachować zmiany ustawień użytkownika.</span><span class="sxs-lookup"><span data-stu-id="e3cd2-103">You can use the `My.Settings.Save` method to persist changes to the user settings.</span></span>  
  
 <span data-ttu-id="e3cd2-104">Zazwyczaj aplikacje są przeznaczone do utrwalania zmian ustawień użytkownika po zamknięciu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e3cd2-104">Typically, applications are designed to persist the changes to the user settings when the application shuts down.</span></span> <span data-ttu-id="e3cd2-105">Wynika to z faktu, że zapisywanie ustawień może zająć, w zależności od kilku czynników, kilka sekund.</span><span class="sxs-lookup"><span data-stu-id="e3cd2-105">This is because saving the settings can take, depending on several factors, several seconds.</span></span>  
  
 <span data-ttu-id="e3cd2-106">Aby uzyskać więcej informacji, zobacz [My. Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span><span class="sxs-lookup"><span data-stu-id="e3cd2-106">For more information, see [My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e3cd2-107">Chociaż można zmienić i zapisać wartości ustawień zakresu użytkownika w czasie wykonywania, ustawienia zakresu aplikacji są tylko do odczytu i nie można ich programowo zmienić.</span><span class="sxs-lookup"><span data-stu-id="e3cd2-107">Although you can change and save the values of user-scope settings at run time, application-scope settings are read-only and cannot be changed programmatically.</span></span> <span data-ttu-id="e3cd2-108">Ustawienia zakresu aplikacji można zmienić podczas tworzenia aplikacji, za pomocą **projektanta projektu**lub edytując plik konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e3cd2-108">You can change application-scope settings when creating the application, through the **Project Designer**, or by editing the application's configuration file.</span></span> <span data-ttu-id="e3cd2-109">Aby uzyskać więcej informacji, zobacz [Zarządzanie ustawieniami aplikacji (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="e3cd2-109">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e3cd2-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="e3cd2-110">Example</span></span>  

 <span data-ttu-id="e3cd2-111">Ten przykład zmienia wartość ustawienia użytkownika `LastChanged` i zapisuje tę zmianę, wywołując metodę `My.Settings.Save`.</span><span class="sxs-lookup"><span data-stu-id="e3cd2-111">This example changes the value of the `LastChanged` user setting and saves that change by calling the `My.Settings.Save` method.</span></span>  
  
 [!code-vb[VbVbalrMyResources#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#5)]  
  
 <span data-ttu-id="e3cd2-112">Aby ten przykład działał, aplikacja musi mieć `LastChanged` ustawienie użytkownika typu `Date`.</span><span class="sxs-lookup"><span data-stu-id="e3cd2-112">For this example to work, your application must have a `LastChanged` user setting, of type `Date`.</span></span> <span data-ttu-id="e3cd2-113">Aby uzyskać więcej informacji, zobacz [Zarządzanie ustawieniami aplikacji (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="e3cd2-113">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3cd2-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e3cd2-114">See also</span></span>

- [<span data-ttu-id="e3cd2-115">My.Settings, obiekt</span><span class="sxs-lookup"><span data-stu-id="e3cd2-115">My.Settings Object</span></span>](../../../../visual-basic/language-reference/objects/my-settings-object.md)
- [<span data-ttu-id="e3cd2-116">Instrukcje: odczytywanie ustawień aplikacji w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e3cd2-116">How to: Read Application Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)
- [<span data-ttu-id="e3cd2-117">Instrukcje: Zmienianie ustawień użytkownika w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e3cd2-117">How to: Change User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)
- [<span data-ttu-id="e3cd2-118">Instrukcje: Tworzenie siatek właściwości dla ustawień użytkownika w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e3cd2-118">How to: Create Property Grids for User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)
- [<span data-ttu-id="e3cd2-119">Zarządzanie ustawieniami aplikacji (.NET)</span><span class="sxs-lookup"><span data-stu-id="e3cd2-119">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)
