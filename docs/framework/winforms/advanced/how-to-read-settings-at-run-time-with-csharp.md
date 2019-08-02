---
title: 'Instrukcje: Czytanie ustawień w czasie wykonywania w języku C#'
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], reading
- application settings [Windows Forms], run time
- application settings [Windows Forms], C#
ms.assetid: dbe8bf09-5e1c-49da-9192-154033d7240b
ms.openlocfilehash: 6a40718d57fad4041eeea2fded03b7256abbe8d1
ms.sourcegitcommit: eb9ff6f364cde6f11322e03800d8f5ce302f3c73
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/01/2019
ms.locfileid: "68710223"
---
# <a name="how-to-read-settings-at-run-time-with-c"></a><span data-ttu-id="669f8-102">Instrukcje: Odczyt ustawień w czasie wykonywania przy użyciu języka C\#</span><span class="sxs-lookup"><span data-stu-id="669f8-102">How To: Read Settings at Run Time With C\#</span></span>

<span data-ttu-id="669f8-103">W czasie wykonywania za pomocą obiektu Properties można odczytać zarówno ustawienia zakresu aplikacji, jak i zakresu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="669f8-103">You can read both Application-scoped and User-scoped settings at run time via the Properties object.</span></span> <span data-ttu-id="669f8-104">Obiekt właściwości uwidacznia wszystkie ustawienia domyślne projektu za pośrednictwem właściwości. Settings. Default w domyślnej przestrzeni nazw projektu, w którym są zdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="669f8-104">The Properties object exposes all of the default settings for the project via the Properties.Settings.Default member in the default namespace of the project they are defined in.</span></span>  
  
## <a name="to-read-settings-at-run-time-with-c"></a><span data-ttu-id="669f8-105">Aby odczytać ustawienia w czasie wykonywania przy użyciu języka C\#</span><span class="sxs-lookup"><span data-stu-id="669f8-105">To Read Settings at Run Time with C\#</span></span>
  
<span data-ttu-id="669f8-106">Uzyskaj dostęp do odpowiedniego ustawienia za pośrednictwem właściwości. Settings. default.</span><span class="sxs-lookup"><span data-stu-id="669f8-106">Access the appropriate setting via the Properties.Settings.Default member.</span></span> <span data-ttu-id="669f8-107">Poniższy przykład pokazuje, jak przypisać ustawienia o nazwie `myColor` do właściwości BackColor.</span><span class="sxs-lookup"><span data-stu-id="669f8-107">The following example shows how to assign a setting named `myColor` to a BackColor property.</span></span> <span data-ttu-id="669f8-108">Wymaga wcześniej utworzenia pliku ustawień zawierającego ustawienie o nazwie `myColor` typu. `System.Drawing.Color`</span><span class="sxs-lookup"><span data-stu-id="669f8-108">It requires you to have previously created a Settings file containing a setting named `myColor` of type `System.Drawing.Color`.</span></span> <span data-ttu-id="669f8-109">Aby uzyskać informacje na temat tworzenia pliku ustawień, [zobacz How to: Utwórz nowe ustawienie w czasie](how-to-create-a-new-setting-at-design-time.md)projektowania.</span><span class="sxs-lookup"><span data-stu-id="669f8-109">For information about creating a Settings file, see [How To: Create a New Setting at Design Time](how-to-create-a-new-setting-at-design-time.md).</span></span>  
  
```csharp
this.BackColor = Properties.Settings.Default.myColor;  
```  
  
## <a name="see-also"></a><span data-ttu-id="669f8-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="669f8-110">See also</span></span>

- [<span data-ttu-id="669f8-111">Używanie ustawień aplikacji i ustawień użytkownika</span><span class="sxs-lookup"><span data-stu-id="669f8-111">Using Application Settings and User Settings</span></span>](using-application-settings-and-user-settings.md)
- [<span data-ttu-id="669f8-112">Instrukcje: Pisanie ustawień użytkownika w czasie wykonywania za pomocąC#</span><span class="sxs-lookup"><span data-stu-id="669f8-112">How To: Write User Settings at Run Time with C#</span></span>](how-to-write-user-settings-at-run-time-with-csharp.md)
- [<span data-ttu-id="669f8-113">Przegląd ustawień aplikacji</span><span class="sxs-lookup"><span data-stu-id="669f8-113">Application Settings Overview</span></span>](application-settings-overview.md)
