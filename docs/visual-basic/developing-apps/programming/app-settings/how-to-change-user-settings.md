---
title: 'Instrukcje: Zmienianie ustawień użytkownika w języku Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- user settings [Visual Basic], changing in Visual Basic
- user settings
- My.Settings object [Visual Basic], changing user settings
- examples [Visual Basic], changing user settings
ms.assetid: 41250181-c594-4854-9988-8183b9eb03cf
ms.openlocfilehash: 05c95026d061918b38cf301209afefa9498e33bf
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58820974"
---
# <a name="how-to-change-user-settings-in-visual-basic"></a><span data-ttu-id="508a7-102">Instrukcje: Zmienianie ustawień użytkownika w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="508a7-102">How to: Change User Settings in Visual Basic</span></span>
<span data-ttu-id="508a7-103">Można zmienić ustawienia użytkownika, przypisując nową wartość do ustawienia właściwości na `My.Settings` obiektu.</span><span class="sxs-lookup"><span data-stu-id="508a7-103">You can change a user setting by assigning a new value to the setting's property on the `My.Settings` object.</span></span>  
  
 <span data-ttu-id="508a7-104">`My.Settings` Obiekt udostępnia każdego ustawienia jako właściwość.</span><span class="sxs-lookup"><span data-stu-id="508a7-104">The `My.Settings` object exposes each setting as a property.</span></span> <span data-ttu-id="508a7-105">Nazwa właściwości jest taka sama jak nazwa ustawienia, a typ właściwości jest taka sama jak typ ustawienia.</span><span class="sxs-lookup"><span data-stu-id="508a7-105">The property name is the same as the setting name, and the property type is the same as the setting type.</span></span> <span data-ttu-id="508a7-106">Ustawienie **zakres** Określa, czy właściwość jest tylko do odczytu: Właściwość dla **aplikacji**— ustawienie zakresu jest tylko do odczytu, podczas właściwość dla **użytkownika**— ustawienie zakresu jest odczytu i zapisu.</span><span class="sxs-lookup"><span data-stu-id="508a7-106">The setting's **Scope** determines if the property is read-only: The property for an **Application**-scope setting is read-only, while the property for a **User**-scope setting is read-write.</span></span> <span data-ttu-id="508a7-107">Aby uzyskać więcej informacji, zobacz [My.Settings — obiekt](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span><span class="sxs-lookup"><span data-stu-id="508a7-107">For more information, see [My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="508a7-108">Mimo że można zmienić i zapisać wartości ustawień zakresu użytkownika w czasie wykonywania, ustawienia zakresu aplikacji są przeznaczone tylko do odczytu i nie można zmienić programowo.</span><span class="sxs-lookup"><span data-stu-id="508a7-108">Although you can change and save the values of user-scope settings at run time, application-scope settings are read-only and cannot be changed programmatically.</span></span> <span data-ttu-id="508a7-109">Ustawienia zakresu aplikacji można zmienić po utworzeniu aplikacji za pomocą **projektanta projektu** lub też edytując plik konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="508a7-109">You can change application-scope settings when you create the application by using the **Project Designer** or by editing the application's configuration file.</span></span> <span data-ttu-id="508a7-110">Aby uzyskać więcej informacji, zobacz [ustawienia zarządzania aplikacji (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="508a7-110">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="example"></a><span data-ttu-id="508a7-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="508a7-111">Example</span></span>  
 <span data-ttu-id="508a7-112">W tym przykładzie zmienia wartość `Nickname` ustawienia użytkownika.</span><span class="sxs-lookup"><span data-stu-id="508a7-112">This example changes the value of the `Nickname` user setting.</span></span>  
  
 [!code-vb[VbVbalrMyResources#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#7)]  
  
 <span data-ttu-id="508a7-113">W tym przykładzie do pracy, aplikacja musi mieć `Nickname` ustawienia użytkownika, typu `String`.</span><span class="sxs-lookup"><span data-stu-id="508a7-113">For this example to work, your application must have a `Nickname` user setting, of type `String`.</span></span>  
  
 <span data-ttu-id="508a7-114">Aplikacja ustawienia użytkownika są zapisywane podczas zamykania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="508a7-114">The application saves the user settings when the application shuts down.</span></span> <span data-ttu-id="508a7-115">Aby zapisać ustawienia natychmiast, należy wywołać `My.Settings.Save` metody.</span><span class="sxs-lookup"><span data-stu-id="508a7-115">To save the settings immediately, call the `My.Settings.Save` method.</span></span> <span data-ttu-id="508a7-116">Aby uzyskać więcej informacji, zobacz [jak: Utrwalanie ustawień użytkownika w języku Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md).</span><span class="sxs-lookup"><span data-stu-id="508a7-116">For more information, see [How to: Persist User Settings in Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="508a7-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="508a7-117">See also</span></span>

- [<span data-ttu-id="508a7-118">My.Settings, obiekt</span><span class="sxs-lookup"><span data-stu-id="508a7-118">My.Settings Object</span></span>](../../../../visual-basic/language-reference/objects/my-settings-object.md)
- [<span data-ttu-id="508a7-119">Instrukcje: Odczytywanie ustawień aplikacji w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="508a7-119">How to: Read Application Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)
- [<span data-ttu-id="508a7-120">Instrukcje: Utrwalanie ustawień użytkownika w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="508a7-120">How to: Persist User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)
- [<span data-ttu-id="508a7-121">Instrukcje: Tworzenie siatek właściwości dla ustawień użytkownika w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="508a7-121">How to: Create Property Grids for User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)
- [<span data-ttu-id="508a7-122">Zarządzanie ustawieniami aplikacji (.NET)</span><span class="sxs-lookup"><span data-stu-id="508a7-122">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)
