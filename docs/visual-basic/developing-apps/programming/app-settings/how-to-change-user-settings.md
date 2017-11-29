---
title: "Porady: zmienianie ustawień użytkownika w Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- user settings [Visual Basic], changing in Visual Basic
- user settings
- My.Settings object [Visual Basic], changing user settings
- examples [Visual Basic], changing user settings
ms.assetid: 41250181-c594-4854-9988-8183b9eb03cf
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: db35a5d63938fcc508c23af5588957d8dc518676
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-change-user-settings-in-visual-basic"></a><span data-ttu-id="503aa-102">Porady: zmienianie ustawień użytkownika w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="503aa-102">How to: Change User Settings in Visual Basic</span></span>
<span data-ttu-id="503aa-103">Ustawienia użytkownika można zmienić, przypisując na nową wartość do ustawienia właściwości `My.Settings` obiektu.</span><span class="sxs-lookup"><span data-stu-id="503aa-103">You can change a user setting by assigning a new value to the setting's property on the `My.Settings` object.</span></span>  
  
 <span data-ttu-id="503aa-104">`My.Settings` Obiekt ujawnia każdego ustawienia jako właściwość.</span><span class="sxs-lookup"><span data-stu-id="503aa-104">The `My.Settings` object exposes each setting as a property.</span></span> <span data-ttu-id="503aa-105">Nazwa właściwości jest taka sama jak nazwa ustawienia i typ właściwości jest taki sam jak typ ustawienia.</span><span class="sxs-lookup"><span data-stu-id="503aa-105">The property name is the same as the setting name, and the property type is the same as the setting type.</span></span> <span data-ttu-id="503aa-106">Ustawienie **zakresu** Określa, czy właściwość jest tylko do odczytu: właściwość **aplikacji**— ustawienie zakresu jest tylko do odczytu, podczas właściwość **użytkownika**-zakresu Ustawienie to odczytu i zapisu.</span><span class="sxs-lookup"><span data-stu-id="503aa-106">The setting's **Scope** determines if the property is read-only: The property for an **Application**-scope setting is read-only, while the property for a **User**-scope setting is read-write.</span></span> <span data-ttu-id="503aa-107">Aby uzyskać więcej informacji, zobacz [My.Settings — obiekt](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span><span class="sxs-lookup"><span data-stu-id="503aa-107">For more information, see [My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="503aa-108">Mimo że można zmienić i zapisać wartości ustawień w zakresie użytkownika w czasie wykonywania, ustawienia zakresu aplikacji są tylko do odczytu i nie można zmienić programowo.</span><span class="sxs-lookup"><span data-stu-id="503aa-108">Although you can change and save the values of user-scope settings at run time, application-scope settings are read-only and cannot be changed programmatically.</span></span> <span data-ttu-id="503aa-109">Ustawienia zakresu aplikacji można zmienić po utworzeniu aplikacji przy użyciu **projektanta projektu** lub poprzez edycję pliku konfiguracyjnego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="503aa-109">You can change application-scope settings when you create the application by using the **Project Designer** or by editing the application's configuration file.</span></span> <span data-ttu-id="503aa-110">Aby uzyskać więcej informacji, zobacz [Zarządzanie ustawieniami aplikacji (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="503aa-110">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="example"></a><span data-ttu-id="503aa-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="503aa-111">Example</span></span>  
 <span data-ttu-id="503aa-112">W tym przykładzie zmienia wartość `Nickname` ustawienia użytkownika.</span><span class="sxs-lookup"><span data-stu-id="503aa-112">This example changes the value of the `Nickname` user setting.</span></span>  
  
 [!code-vb[VbVbalrMyResources#7](../../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/how-to-change-user-settings_1.vb)]  
  
 <span data-ttu-id="503aa-113">W tym przykładzie działała, aplikacja musi mieć `Nickname` ustawienia użytkownika, typu `String`.</span><span class="sxs-lookup"><span data-stu-id="503aa-113">For this example to work, your application must have a `Nickname` user setting, of type `String`.</span></span>  
  
 <span data-ttu-id="503aa-114">Aplikacja zapisuje ustawienia użytkownika podczas zamykania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="503aa-114">The application saves the user settings when the application shuts down.</span></span> <span data-ttu-id="503aa-115">Aby zapisać ustawienia natychmiast, należy wywołać `My.Settings.Save` metody.</span><span class="sxs-lookup"><span data-stu-id="503aa-115">To save the settings immediately, call the `My.Settings.Save` method.</span></span> <span data-ttu-id="503aa-116">Aby uzyskać więcej informacji, zobacz [porady: utrwalanie ustawień użytkownika w języku Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md).</span><span class="sxs-lookup"><span data-stu-id="503aa-116">For more information, see [How to: Persist User Settings in Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="503aa-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="503aa-117">See Also</span></span>  
 [<span data-ttu-id="503aa-118">My.Settings — obiekt</span><span class="sxs-lookup"><span data-stu-id="503aa-118">My.Settings Object</span></span>](../../../../visual-basic/language-reference/objects/my-settings-object.md)  
 [<span data-ttu-id="503aa-119">Porady: odczytywanie ustawień aplikacji w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="503aa-119">How to: Read Application Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)  
 [<span data-ttu-id="503aa-120">Porady: utrwalanie ustawień użytkownika w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="503aa-120">How to: Persist User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)  
 [<span data-ttu-id="503aa-121">Porady: tworzenie siatek właściwości dla ustawień użytkownika w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="503aa-121">How to: Create Property Grids for User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)  
 [<span data-ttu-id="503aa-122">Zarządzanie ustawieniami aplikacji (.NET)</span><span class="sxs-lookup"><span data-stu-id="503aa-122">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)
