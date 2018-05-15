---
title: 'Porady: pisanie ustawień użytkownika w czasie wykonywania w języku C#'
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], run time
- application settings [Windows Forms], writing user settings
- application settings [Windows Forms], C#
ms.assetid: 9d061c7d-b33b-470f-a36d-edccb1d6f9a3
ms.openlocfilehash: f289b6a6a4a726ffa6bb2c9df99c665e2872e8d5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-write-user-settings-at-run-time-with-c"></a><span data-ttu-id="7eddf-102">Porady: pisanie ustawień użytkownika w czasie wykonywania w języku C#</span><span class="sxs-lookup"><span data-stu-id="7eddf-102">How To: Write User Settings at Run Time with C#</span></span> #
<span data-ttu-id="7eddf-103">Ustawienia, które są zakresu aplikacji są tylko do odczytu, a można zmienić tylko w czasie projektowania lub przez zmodyfikowanie pliku .config między sesjami aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7eddf-103">Settings that are application-scoped are read-only, and can only be changed at design time or by altering the .config file in between application sessions.</span></span> <span data-ttu-id="7eddf-104">Ustawienia, które są zakresu użytkownika, jednak mogą być zapisywane w czasie wykonywania tak samo, jak można zmienić wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="7eddf-104">Settings that are user-scoped, however, can be written at run time just as you would change any property value.</span></span> <span data-ttu-id="7eddf-105">Nowa wartość będzie się powtarzać, w czasie trwania sesji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7eddf-105">The new value persists for the duration of the application session.</span></span> <span data-ttu-id="7eddf-106">Można ją utrwalić ustawienia między sesjami aplikacji przez wywołanie metody Zapisz zmiany.</span><span class="sxs-lookup"><span data-stu-id="7eddf-106">You can persist the changes to the settings between application sessions by calling the Save method.</span></span>  
  
### <a name="how-to-write-and-persist-user-settings-at-run-time-with-c"></a><span data-ttu-id="7eddf-107">Porady: Pisanie i utrzymania ustawień użytkownika w czasie wykonywania w języku C#</span><span class="sxs-lookup"><span data-stu-id="7eddf-107">How To: Write and Persist User Settings at Run Time with C#</span></span>  
  
1.  <span data-ttu-id="7eddf-108">Ustawienia dostępu i przypisz mu nową wartość, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="7eddf-108">Access the setting and assign it a new value as shown in this example:</span></span>  
  
    ```  
    // C#  
    Properties.Settings.Default.myColor = Color.AliceBlue;  
    ```  
  
2.  <span data-ttu-id="7eddf-109">Jeśli chcesz utrwalić zmiany ustawienia między sesjami aplikacji, wywołaj metodę Save jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="7eddf-109">If you want to persist the changes to the settings between application sessions, call the Save method as shown in this example:</span></span>  
  
    ```  
    // C#  
    Properties.Settings.Default.Save();  
    ```  
  
     <span data-ttu-id="7eddf-110">Ustawienia użytkownika są zapisywane w pliku w podfolderze folderu danych aplikacji lokalnej ukryty przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="7eddf-110">User settings are saved in a file within a subfolder of the user’s local hidden application data folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7eddf-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7eddf-111">See Also</span></span>  
 [<span data-ttu-id="7eddf-112">Używanie ustawień aplikacji i ustawień użytkownika</span><span class="sxs-lookup"><span data-stu-id="7eddf-112">Using Application Settings and User Settings</span></span>](../../../../docs/framework/winforms/advanced/using-application-settings-and-user-settings.md)  
 [<span data-ttu-id="7eddf-113">Instrukcje: czytanie ustawień w czasie wykonywania w języku C#</span><span class="sxs-lookup"><span data-stu-id="7eddf-113">How To: Read Settings at Run Time With C#</span></span>](../../../../docs/framework/winforms/advanced/how-to-read-settings-at-run-time-with-csharp.md)  
 [<span data-ttu-id="7eddf-114">Przegląd ustawień aplikacji</span><span class="sxs-lookup"><span data-stu-id="7eddf-114">Application Settings Overview</span></span>](../../../../docs/framework/winforms/advanced/application-settings-overview.md)
