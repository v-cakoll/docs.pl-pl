---
title: 'Instrukcje: Odczytaj ustawienia w czasie wykonywania za pomocąC#'
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], reading
- application settings [Windows Forms], run time
- application settings [Windows Forms], C#
ms.assetid: dbe8bf09-5e1c-49da-9192-154033d7240b
ms.openlocfilehash: 8cdc1a79f1ab327ae037cd6a04aa769196405127
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56974851"
---
# <a name="how-to-read-settings-at-run-time-with-c"></a><span data-ttu-id="df8c6-102">Instrukcje: Odczytaj ustawienia w czasie wykonywania przy użyciu języka C\#</span><span class="sxs-lookup"><span data-stu-id="df8c6-102">How To: Read Settings at Run Time With C\#</span></span>

<span data-ttu-id="df8c6-103">W czasie wykonywania za pomocą obiektu właściwości można odczytać ustawień o zakresie aplikacji i zakresie użytkownika.</span><span class="sxs-lookup"><span data-stu-id="df8c6-103">You can read both Application-scoped and User-scoped settings at run time via the Properties object.</span></span> <span data-ttu-id="df8c6-104">Obiekt właściwości udostępnia wszystkie ustawienia domyślne dla projektu za pomocą elementu członkowskiego Properties.Settings.Default.</span><span class="sxs-lookup"><span data-stu-id="df8c6-104">The Properties object exposes all of the default settings for the project via the Properties.Settings.Default member.</span></span>  
  
## <a name="to-read-settings-at-run-time-with-c"></a><span data-ttu-id="df8c6-105">Do odczytywania ustawień w czasie wykonywania przy użyciu języka C\#</span><span class="sxs-lookup"><span data-stu-id="df8c6-105">To Read Settings at Run Time with C\#</span></span>
  
<span data-ttu-id="df8c6-106">Dostęp do odpowiedniego ustawienia za pomocą elementu członkowskiego Properties.Settings.Default.</span><span class="sxs-lookup"><span data-stu-id="df8c6-106">Access the appropriate setting via the Properties.Settings.Default member.</span></span> <span data-ttu-id="df8c6-107">Poniższy przykład pokazuje, jak przypisać ustawienie o nazwie `myColor` właściwości BackColor.</span><span class="sxs-lookup"><span data-stu-id="df8c6-107">The following example shows how to assign a setting named `myColor` to a BackColor property.</span></span> <span data-ttu-id="df8c6-108">Musisz wcześniej utworzono plik ustawień zawierający ustawienia o nazwie `myColor` typu `System.Drawing.Color`.</span><span class="sxs-lookup"><span data-stu-id="df8c6-108">It requires you to have previously created a Settings file containing a setting named `myColor` of type `System.Drawing.Color`.</span></span> <span data-ttu-id="df8c6-109">Aby uzyskać informacje dotyczące tworzenia pliku ustawień, zobacz [How to: Utwórz nowe ustawienie w czasie projektowania](how-to-create-a-new-setting-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="df8c6-109">For information about creating a Settings file, see [How To: Create a New Setting at Design Time](how-to-create-a-new-setting-at-design-time.md).</span></span>  
  
```csharp
this.BackColor = Properties.Settings.Default.myColor;  
```  
  
## <a name="see-also"></a><span data-ttu-id="df8c6-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="df8c6-110">See also</span></span>

- [<span data-ttu-id="df8c6-111">Używanie ustawień aplikacji i ustawień użytkownika</span><span class="sxs-lookup"><span data-stu-id="df8c6-111">Using Application Settings and User Settings</span></span>](using-application-settings-and-user-settings.md)
- [<span data-ttu-id="df8c6-112">Instrukcje: Pisanie ustawień użytkownika w czasie wykonywania w językuC#</span><span class="sxs-lookup"><span data-stu-id="df8c6-112">How To: Write User Settings at Run Time with C#</span></span>](how-to-write-user-settings-at-run-time-with-csharp.md)
- [<span data-ttu-id="df8c6-113">Przegląd ustawień aplikacji</span><span class="sxs-lookup"><span data-stu-id="df8c6-113">Application Settings Overview</span></span>](application-settings-overview.md)
