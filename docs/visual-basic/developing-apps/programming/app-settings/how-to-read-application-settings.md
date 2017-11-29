---
title: "Porady: odczytywanie ustawień aplikacji w Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- reading application settings
- My.Settings object [Visual Basic], reading application settings
- application settings [Visual Basic], reading
ms.assetid: eb3428ef-115e-49a8-a878-e0613183fee0
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ea6cfc529262053daf7c8111271de2c51e9cab4e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-read-application-settings-in-visual-basic"></a><span data-ttu-id="11e02-102">Porady: odczytywanie ustawień aplikacji w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="11e02-102">How to: Read Application Settings in Visual Basic</span></span>
<span data-ttu-id="11e02-103">Ustawienia użytkownika może być odczytany przez uzyskiwanie dostępu do ustawiania właściwości na `My.Settings` obiektu.</span><span class="sxs-lookup"><span data-stu-id="11e02-103">You can read a user setting by accessing the setting's property on the `My.Settings` object.</span></span>  
  
 <span data-ttu-id="11e02-104">`My.Settings` Obiekt ujawnia każdego ustawienia jako właściwość.</span><span class="sxs-lookup"><span data-stu-id="11e02-104">The `My.Settings` object exposes each setting as a property.</span></span> <span data-ttu-id="11e02-105">Nazwa właściwości jest taka sama jak nazwa ustawienia i typ właściwości jest taki sam jak typ ustawienia.</span><span class="sxs-lookup"><span data-stu-id="11e02-105">The property name is the same as the setting name, and the property type is the same as the setting type.</span></span> <span data-ttu-id="11e02-106">Tego ustawienia **zakresu** wskazuje, czy właściwość jest tylko do odczytu; właściwość **aplikacji** ustawienie zakresu jest tylko do odczytu, podczas właściwość **użytkownika** zakres ustawienie jest do odczytu / zapisu.</span><span class="sxs-lookup"><span data-stu-id="11e02-106">The setting's **Scope** indicates if the property is read-only; the property for an **Application** scope setting is read-only, while the property for a **User** scope setting is read-write.</span></span> <span data-ttu-id="11e02-107">Aby uzyskać więcej informacji, zobacz [My.Settings — obiekt](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span><span class="sxs-lookup"><span data-stu-id="11e02-107">For more information, see [My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="11e02-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="11e02-108">Example</span></span>  
 <span data-ttu-id="11e02-109">W tym przykładzie wyświetlono wartości `Nickname` ustawienie.</span><span class="sxs-lookup"><span data-stu-id="11e02-109">This example displays the value of the `Nickname` setting.</span></span>  
  
 [!code-vb[VbVbalrMyResources#14](../../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/how-to-read-application-settings_1.vb)]  
  
 <span data-ttu-id="11e02-110">W tym przykładzie działała, aplikacja musi mieć `Nickname` ustawienia typu `String`.</span><span class="sxs-lookup"><span data-stu-id="11e02-110">For this example to work, your application must have a `Nickname` setting, of type `String`.</span></span> <span data-ttu-id="11e02-111">Aby uzyskać więcej informacji, zobacz [Zarządzanie ustawieniami aplikacji (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="11e02-111">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11e02-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="11e02-112">See Also</span></span>  
 [<span data-ttu-id="11e02-113">My.Settings — obiekt</span><span class="sxs-lookup"><span data-stu-id="11e02-113">My.Settings Object</span></span>](../../../../visual-basic/language-reference/objects/my-settings-object.md)  
 [<span data-ttu-id="11e02-114">Porady: Zmienianie ustawień użytkownika w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="11e02-114">How to: Change User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)  
 [<span data-ttu-id="11e02-115">Porady: utrwalanie ustawień użytkownika w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="11e02-115">How to: Persist User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)  
 [<span data-ttu-id="11e02-116">Porady: tworzenie siatek właściwości dla ustawień użytkownika w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="11e02-116">How to: Create Property Grids for User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)  
 [<span data-ttu-id="11e02-117">Zarządzanie ustawieniami aplikacji (.NET)</span><span class="sxs-lookup"><span data-stu-id="11e02-117">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)
