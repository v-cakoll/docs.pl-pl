---
title: 'Instrukcje: Utrwalanie ustawień użytkownika w języku Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Settings object [Visual Basic], persisting user settings
- persistence [Visual Basic], persisting user settings [Visual Basic]
- user settings [Visual Basic], persisting
ms.assetid: 0e5e6415-b6e2-4602-9be0-a65fa167d007
ms.openlocfilehash: 35997db52a59aeaff5a2c404ea83b15639ea23a0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58825184"
---
# <a name="how-to-persist-user-settings-in-visual-basic"></a><span data-ttu-id="c0b6e-102">Instrukcje: Utrwalanie ustawień użytkownika w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c0b6e-102">How to: Persist User Settings in Visual Basic</span></span>
<span data-ttu-id="c0b6e-103">Możesz użyć `My.Settings.Save` metodę, aby utrwalić zmiany ustawień użytkownika.</span><span class="sxs-lookup"><span data-stu-id="c0b6e-103">You can use the `My.Settings.Save` method to persist changes to the user settings.</span></span>  
  
 <span data-ttu-id="c0b6e-104">Zazwyczaj aplikacje są przeznaczone do utrwalenia zmiany w ustawieniach użytkownika podczas zamykania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c0b6e-104">Typically, applications are designed to persist the changes to the user settings when the application shuts down.</span></span> <span data-ttu-id="c0b6e-105">Jest to spowodowane zapisywania ustawień może potrwać, w zależności od kilku czynników, w kilka sekund.</span><span class="sxs-lookup"><span data-stu-id="c0b6e-105">This is because saving the settings can take, depending on several factors, several seconds.</span></span>  
  
 <span data-ttu-id="c0b6e-106">Aby uzyskać więcej informacji, zobacz [My.Settings — obiekt](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span><span class="sxs-lookup"><span data-stu-id="c0b6e-106">For more information, see [My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c0b6e-107">Mimo że można zmienić i zapisać wartości ustawień zakresu użytkownika w czasie wykonywania, ustawienia zakresu aplikacji są przeznaczone tylko do odczytu i nie można zmienić programowo.</span><span class="sxs-lookup"><span data-stu-id="c0b6e-107">Although you can change and save the values of user-scope settings at run time, application-scope settings are read-only and cannot be changed programmatically.</span></span> <span data-ttu-id="c0b6e-108">Możesz zmienić ustawienia zakres aplikacji, podczas tworzenia aplikacji, za pośrednictwem **projektanta projektu**, lub też edytując plik konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c0b6e-108">You can change application-scope settings when creating the application, through the **Project Designer**, or by editing the application's configuration file.</span></span> <span data-ttu-id="c0b6e-109">Aby uzyskać więcej informacji, zobacz [ustawienia zarządzania aplikacji (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="c0b6e-109">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c0b6e-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="c0b6e-110">Example</span></span>  
 <span data-ttu-id="c0b6e-111">W tym przykładzie zmienia wartość `LastChanged` ustawienia użytkownika i zapisuje, które zmieniają się przez wywołanie metody `My.Settings.Save` metody.</span><span class="sxs-lookup"><span data-stu-id="c0b6e-111">This example changes the value of the `LastChanged` user setting and saves that change by calling the `My.Settings.Save` method.</span></span>  
  
 [!code-vb[VbVbalrMyResources#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#5)]  
  
 <span data-ttu-id="c0b6e-112">W tym przykładzie do pracy, aplikacja musi mieć `LastChanged` ustawienia użytkownika, typu `Date`.</span><span class="sxs-lookup"><span data-stu-id="c0b6e-112">For this example to work, your application must have a `LastChanged` user setting, of type `Date`.</span></span> <span data-ttu-id="c0b6e-113">Aby uzyskać więcej informacji, zobacz [ustawienia zarządzania aplikacji (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="c0b6e-113">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0b6e-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c0b6e-114">See also</span></span>

- [<span data-ttu-id="c0b6e-115">My.Settings, obiekt</span><span class="sxs-lookup"><span data-stu-id="c0b6e-115">My.Settings Object</span></span>](../../../../visual-basic/language-reference/objects/my-settings-object.md)
- [<span data-ttu-id="c0b6e-116">Instrukcje: Odczytywanie ustawień aplikacji w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c0b6e-116">How to: Read Application Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)
- [<span data-ttu-id="c0b6e-117">Instrukcje: Zmienianie ustawień użytkownika w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c0b6e-117">How to: Change User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)
- [<span data-ttu-id="c0b6e-118">Instrukcje: Tworzenie siatek właściwości dla ustawień użytkownika w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c0b6e-118">How to: Create Property Grids for User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)
- [<span data-ttu-id="c0b6e-119">Zarządzanie ustawieniami aplikacji (.NET)</span><span class="sxs-lookup"><span data-stu-id="c0b6e-119">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)
