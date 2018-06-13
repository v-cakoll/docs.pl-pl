---
title: 'Porady: czytanie ustawień w czasie wykonywania w języku C#'
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], reading
- application settings [Windows Forms], run time
- application settings [Windows Forms], C#
ms.assetid: dbe8bf09-5e1c-49da-9192-154033d7240b
ms.openlocfilehash: 8259e2f429718793c01868855651d1000620fae5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33521017"
---
# <a name="how-to-read-settings-at-run-time-with-c"></a><span data-ttu-id="2fc9d-102">Porady: czytanie ustawień w czasie wykonywania w języku C#</span><span class="sxs-lookup"><span data-stu-id="2fc9d-102">How To: Read Settings at Run Time With C#</span></span> #
<span data-ttu-id="2fc9d-103">W czasie wykonywania za pośrednictwem właściwości obiektu można odczytać ustawień zarówno zakresu aplikacji i zakresu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="2fc9d-103">You can read both Application-scoped and User-scoped settings at run time via the Properties object.</span></span> <span data-ttu-id="2fc9d-104">Obiekt właściwości udostępnia wszystkie ustawienia domyślne dla projektu za pomocą elementu członkowskiego Properties.Settings.Default.</span><span class="sxs-lookup"><span data-stu-id="2fc9d-104">The Properties object exposes all of the default settings for the project via the Properties.Settings.Default member.</span></span>  
  
### <a name="to-read-settings-at-run-time-with-c"></a><span data-ttu-id="2fc9d-105">Aby odczytać ustawień w czasie wykonywania w języku C#</span><span class="sxs-lookup"><span data-stu-id="2fc9d-105">To Read Settings at Run Time with C#</span></span>  
  
-   <span data-ttu-id="2fc9d-106">Dostęp za pośrednictwem elementu członkowskiego Properties.Settings.Default odpowiednie ustawienia.</span><span class="sxs-lookup"><span data-stu-id="2fc9d-106">Access the appropriate setting via the Properties.Settings.Default member.</span></span> <span data-ttu-id="2fc9d-107">Poniższy przykład przedstawia sposób przypisać ustawienie o nazwie `myColor` właściwości BackColor.</span><span class="sxs-lookup"><span data-stu-id="2fc9d-107">The following example shows how to assign a setting named `myColor` to a BackColor property.</span></span> <span data-ttu-id="2fc9d-108">Użytkownik musi mieć wcześniej utworzony plik ustawień zawierający ustawienie o nazwie `myColor` typu `System.Drawing.Color`.</span><span class="sxs-lookup"><span data-stu-id="2fc9d-108">It requires you to have previously created a Settings file containing a setting named `myColor` of type `System.Drawing.Color`.</span></span> <span data-ttu-id="2fc9d-109">Aby uzyskać informacje dotyczące tworzenia pliku ustawień, zobacz [jak: utworzyć nowe ustawienie w czasie projektowania](../../../../docs/framework/winforms/advanced/how-to-create-a-new-setting-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="2fc9d-109">For information about creating a Settings file, see [How To: Create a New Setting at Design Time](../../../../docs/framework/winforms/advanced/how-to-create-a-new-setting-at-design-time.md).</span></span>  
  
    ```  
    // C#  
    this.BackColor = Properties.Settings.Default.myColor;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="2fc9d-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2fc9d-110">See Also</span></span>  
 [<span data-ttu-id="2fc9d-111">Używanie ustawień aplikacji i ustawień użytkownika</span><span class="sxs-lookup"><span data-stu-id="2fc9d-111">Using Application Settings and User Settings</span></span>](../../../../docs/framework/winforms/advanced/using-application-settings-and-user-settings.md)  
 [<span data-ttu-id="2fc9d-112">Instrukcje: pisanie ustawień użytkownika w czasie wykonywania w języku C#</span><span class="sxs-lookup"><span data-stu-id="2fc9d-112">How To: Write User Settings at Run Time with C#</span></span>](../../../../docs/framework/winforms/advanced/how-to-write-user-settings-at-run-time-with-csharp.md)  
 [<span data-ttu-id="2fc9d-113">Przegląd ustawień aplikacji</span><span class="sxs-lookup"><span data-stu-id="2fc9d-113">Application Settings Overview</span></span>](../../../../docs/framework/winforms/advanced/application-settings-overview.md)
