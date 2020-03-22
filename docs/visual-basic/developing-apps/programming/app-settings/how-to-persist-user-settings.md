---
title: 'Instrukcje: utrwalanie ustawień użytkownika'
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
# <a name="how-to-persist-user-settings-in-visual-basic"></a><span data-ttu-id="28027-102">Porady: utrwalanie ustawień użytkownika w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="28027-102">How to: Persist User Settings in Visual Basic</span></span>

<span data-ttu-id="28027-103">Za pomocą `My.Settings.Save` tej metody można utrwalić zmiany w ustawieniach użytkownika.</span><span class="sxs-lookup"><span data-stu-id="28027-103">You can use the `My.Settings.Save` method to persist changes to the user settings.</span></span>  
  
 <span data-ttu-id="28027-104">Zazwyczaj aplikacje są przeznaczone do utrwalania zmian w ustawieniach użytkownika, gdy aplikacja zostanie zamknięta.</span><span class="sxs-lookup"><span data-stu-id="28027-104">Typically, applications are designed to persist the changes to the user settings when the application shuts down.</span></span> <span data-ttu-id="28027-105">Dzieje się tak dlatego, że zapisanie ustawień może potrwać, w zależności od kilku czynników, kilka sekund.</span><span class="sxs-lookup"><span data-stu-id="28027-105">This is because saving the settings can take, depending on several factors, several seconds.</span></span>  
  
 <span data-ttu-id="28027-106">Aby uzyskać więcej informacji, zobacz [Obiekt My.Settings](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span><span class="sxs-lookup"><span data-stu-id="28027-106">For more information, see [My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="28027-107">Chociaż można zmienić i zapisać wartości ustawień zakresu użytkownika w czasie wykonywania, ustawienia zakresu aplikacji są tylko do odczytu i nie można zmienić programowo.</span><span class="sxs-lookup"><span data-stu-id="28027-107">Although you can change and save the values of user-scope settings at run time, application-scope settings are read-only and cannot be changed programmatically.</span></span> <span data-ttu-id="28027-108">Ustawienia zakresu aplikacji można zmienić podczas tworzenia aplikacji za pośrednictwem **projektanta projektu**lub edytowania pliku konfiguracyjnego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="28027-108">You can change application-scope settings when creating the application, through the **Project Designer**, or by editing the application's configuration file.</span></span> <span data-ttu-id="28027-109">Aby uzyskać więcej informacji, zobacz [Zarządzanie ustawieniami aplikacji (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="28027-109">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="example"></a><span data-ttu-id="28027-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="28027-110">Example</span></span>  

 <span data-ttu-id="28027-111">W tym przykładzie `LastChanged` zmienia wartość ustawienia użytkownika i `My.Settings.Save` zapisuje tę zmianę, wywołując metodę.</span><span class="sxs-lookup"><span data-stu-id="28027-111">This example changes the value of the `LastChanged` user setting and saves that change by calling the `My.Settings.Save` method.</span></span>  
  
 [!code-vb[VbVbalrMyResources#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#5)]  
  
 <span data-ttu-id="28027-112">W tym przykładzie do pracy `LastChanged` aplikacja musi mieć `Date`ustawienie użytkownika, typu .</span><span class="sxs-lookup"><span data-stu-id="28027-112">For this example to work, your application must have a `LastChanged` user setting, of type `Date`.</span></span> <span data-ttu-id="28027-113">Aby uzyskać więcej informacji, zobacz [Zarządzanie ustawieniami aplikacji (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="28027-113">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28027-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="28027-114">See also</span></span>

- [<span data-ttu-id="28027-115">My.Settings, obiekt</span><span class="sxs-lookup"><span data-stu-id="28027-115">My.Settings Object</span></span>](../../../../visual-basic/language-reference/objects/my-settings-object.md)
- [<span data-ttu-id="28027-116">Porady: odczytywanie ustawień aplikacji w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="28027-116">How to: Read Application Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)
- [<span data-ttu-id="28027-117">Porady: zmienianie ustawień użytkownika w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="28027-117">How to: Change User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)
- [<span data-ttu-id="28027-118">Porady: tworzenie siatek właściwości dla ustawień użytkownika w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="28027-118">How to: Create Property Grids for User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)
- [<span data-ttu-id="28027-119">Zarządzanie ustawieniami aplikacji (.NET)</span><span class="sxs-lookup"><span data-stu-id="28027-119">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)
