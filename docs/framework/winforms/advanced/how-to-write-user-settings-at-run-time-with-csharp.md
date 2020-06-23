---
title: 'Porady: pisanie ustawień użytkownika w czasie wykonywania w języku C#'
description: Informacje o sposobie pisania ustawień w czasie wykonywania w języku C# poprzez Utrwalanie zmian ustawień między sesjami aplikacji przez wywołanie metody Save.
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], run time
- application settings [Windows Forms], writing user settings
- application settings [Windows Forms], C#
ms.assetid: 9d061c7d-b33b-470f-a36d-edccb1d6f9a3
ms.openlocfilehash: 6154ff1b92d6c2d4c788299e59eb8f73e6b69c4b
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904328"
---
# <a name="how-to-write-user-settings-at-run-time-with-c"></a><span data-ttu-id="c06c8-103">Instrukcje: pisanie ustawień użytkownika w czasie wykonywania przy użyciu języka C\#</span><span class="sxs-lookup"><span data-stu-id="c06c8-103">How To: Write User Settings at Run Time with C\#</span></span>

<span data-ttu-id="c06c8-104">Ustawienia, które są objęte zakresem aplikacji, są tylko do odczytu i mogą być zmieniane tylko w czasie projektowania lub przez zmianę pliku. config między sesjami aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c06c8-104">Settings that are application-scoped are read-only, and can only be changed at design time or by altering the .config file in between application sessions.</span></span> <span data-ttu-id="c06c8-105">Ustawienia, które są objęte zakresem użytkownika, można jednak zapisywać w czasie wykonywania tak samo jak w przypadku zmiany dowolnej wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="c06c8-105">Settings that are user-scoped, however, can be written at run time just as you would change any property value.</span></span> <span data-ttu-id="c06c8-106">Nowa wartość będzie trwała w czasie trwania sesji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c06c8-106">The new value persists for the duration of the application session.</span></span> <span data-ttu-id="c06c8-107">Zmiany ustawień między sesjami aplikacji można zachować, wywołując metodę Save.</span><span class="sxs-lookup"><span data-stu-id="c06c8-107">You can persist the changes to the settings between application sessions by calling the Save method.</span></span>  
  
## <a name="how-to-write-and-persist-user-settings-at-run-time-with-c"></a><span data-ttu-id="c06c8-108">Instrukcje: zapisywanie i utrwalanie ustawień użytkownika w czasie wykonywania przy użyciu języka C\#</span><span class="sxs-lookup"><span data-stu-id="c06c8-108">How To: Write and Persist User Settings at Run Time with C\#</span></span>
  
1. <span data-ttu-id="c06c8-109">Uzyskaj dostęp do tego ustawienia i przypisz go nową wartość, jak pokazano w tym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="c06c8-109">Access the setting and assign it a new value as shown in this example:</span></span>  
  
   ```csharp
   Properties.Settings.Default.myColor = Color.AliceBlue;  
   ```  
  
2. <span data-ttu-id="c06c8-110">Jeśli chcesz zachować zmiany ustawień między sesjami aplikacji, wywołaj metodę Save, jak pokazano w tym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="c06c8-110">If you want to persist the changes to the settings between application sessions, call the Save method as shown in this example:</span></span>  
  
    ```csharp
    Properties.Settings.Default.Save();  
    ```  
  
<span data-ttu-id="c06c8-111">Ustawienia użytkownika są zapisywane w pliku w podfolderze w lokalnym ukrytym folderze dane aplikacji użytkownika.</span><span class="sxs-lookup"><span data-stu-id="c06c8-111">User settings are saved in a file within a subfolder of the user’s local hidden application data folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c06c8-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c06c8-112">See also</span></span>

- [<span data-ttu-id="c06c8-113">Używanie ustawień aplikacji i ustawień użytkownika</span><span class="sxs-lookup"><span data-stu-id="c06c8-113">Using Application Settings and User Settings</span></span>](using-application-settings-and-user-settings.md)
- [<span data-ttu-id="c06c8-114">Porady: czytanie ustawień w czasie wykonywania w języku C#</span><span class="sxs-lookup"><span data-stu-id="c06c8-114">How To: Read Settings at Run Time With C#</span></span>](how-to-read-settings-at-run-time-with-csharp.md)
- [<span data-ttu-id="c06c8-115">Przegląd ustawień aplikacji</span><span class="sxs-lookup"><span data-stu-id="c06c8-115">Application Settings Overview</span></span>](application-settings-overview.md)
