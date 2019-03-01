---
title: 'Instrukcje: Pisanie ustawień użytkownika w czasie wykonywania w językuC#'
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], run time
- application settings [Windows Forms], writing user settings
- application settings [Windows Forms], C#
ms.assetid: 9d061c7d-b33b-470f-a36d-edccb1d6f9a3
ms.openlocfilehash: 264fa9706f9255d7324cad6d02c36cc424e28995
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56981598"
---
# <a name="how-to-write-user-settings-at-run-time-with-c"></a><span data-ttu-id="3e9b3-102">Instrukcje: Pisanie ustawień użytkownika w czasie wykonywania w języku C\#</span><span class="sxs-lookup"><span data-stu-id="3e9b3-102">How To: Write User Settings at Run Time with C\#</span></span>

<span data-ttu-id="3e9b3-103">Ustawienia, które są w zakresie aplikacji są przeznaczone tylko do odczytu, a następnie można zmienić tylko w czasie projektowania lub przez zmianę w pliku config między sesjami aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3e9b3-103">Settings that are application-scoped are read-only, and can only be changed at design time or by altering the .config file in between application sessions.</span></span> <span data-ttu-id="3e9b3-104">Ustawienia, które są z zakresu użytkownika, jednak mogą być zapisywane w czasie wykonywania tak samo, jak należy zmienić dowolnej wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="3e9b3-104">Settings that are user-scoped, however, can be written at run time just as you would change any property value.</span></span> <span data-ttu-id="3e9b3-105">Nowa wartość będzie się powtarzać, czas trwania sesji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3e9b3-105">The new value persists for the duration of the application session.</span></span> <span data-ttu-id="3e9b3-106">Jednak można utrwalić zmiany ustawienia między sesjami aplikacji przez wywołanie metody zapisu.</span><span class="sxs-lookup"><span data-stu-id="3e9b3-106">You can persist the changes to the settings between application sessions by calling the Save method.</span></span>  
  
## <a name="how-to-write-and-persist-user-settings-at-run-time-with-c"></a><span data-ttu-id="3e9b3-107">Instrukcje: Pisanie i utrwalanie ustawień użytkownika w czasie wykonywania przy użyciu języka C\#</span><span class="sxs-lookup"><span data-stu-id="3e9b3-107">How To: Write and Persist User Settings at Run Time with C\#</span></span>
  
1. <span data-ttu-id="3e9b3-108">Ustawienia dostępu i przypisz mu nową wartość, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="3e9b3-108">Access the setting and assign it a new value as shown in this example:</span></span>  
  
   ```csharp
   Properties.Settings.Default.myColor = Color.AliceBlue;  
   ```  
  
2. <span data-ttu-id="3e9b3-109">Jeśli chcesz utrwalić zmiany ustawienia między sesjami aplikacji, należy wywołać metodę zapisywania, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="3e9b3-109">If you want to persist the changes to the settings between application sessions, call the Save method as shown in this example:</span></span>  
  
    ```csharp
    Properties.Settings.Default.Save();  
    ```  
  
<span data-ttu-id="3e9b3-110">Ustawienia użytkownika są zapisywane w pliku w podfolderze folderu lokalnego aplikacji ukryty przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="3e9b3-110">User settings are saved in a file within a subfolder of the user’s local hidden application data folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e9b3-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3e9b3-111">See also</span></span>

- [<span data-ttu-id="3e9b3-112">Używanie ustawień aplikacji i ustawień użytkownika</span><span class="sxs-lookup"><span data-stu-id="3e9b3-112">Using Application Settings and User Settings</span></span>](using-application-settings-and-user-settings.md)
- [<span data-ttu-id="3e9b3-113">Instrukcje: Odczytaj ustawienia w czasie wykonywania za pomocąC#</span><span class="sxs-lookup"><span data-stu-id="3e9b3-113">How To: Read Settings at Run Time With C#</span></span>](how-to-read-settings-at-run-time-with-csharp.md)
- [<span data-ttu-id="3e9b3-114">Przegląd ustawień aplikacji</span><span class="sxs-lookup"><span data-stu-id="3e9b3-114">Application Settings Overview</span></span>](application-settings-overview.md)
