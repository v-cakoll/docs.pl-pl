---
title: "Porady: czytanie ustawień w czasie wykonywania w języku C#"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application settings [Windows Forms], reading
- application settings [Windows Forms], run time
- application settings [Windows Forms], C#
ms.assetid: dbe8bf09-5e1c-49da-9192-154033d7240b
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 85dc3a2c97b8fe5003c6026874dbdcaa9af89d77
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-read-settings-at-run-time-with-c"></a><span data-ttu-id="b222a-102">Porady: czytanie ustawień w czasie wykonywania w języku C#</span><span class="sxs-lookup"><span data-stu-id="b222a-102">How To: Read Settings at Run Time With C#</span></span> #
<span data-ttu-id="b222a-103">W czasie wykonywania za pośrednictwem właściwości obiektu można odczytać ustawień zarówno zakresu aplikacji i zakresu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="b222a-103">You can read both Application-scoped and User-scoped settings at run time via the Properties object.</span></span> <span data-ttu-id="b222a-104">Obiekt właściwości udostępnia wszystkie ustawienia domyślne dla projektu za pomocą elementu członkowskiego Properties.Settings.Default.</span><span class="sxs-lookup"><span data-stu-id="b222a-104">The Properties object exposes all of the default settings for the project via the Properties.Settings.Default member.</span></span>  
  
### <a name="to-read-settings-at-run-time-with-c"></a><span data-ttu-id="b222a-105">Aby odczytać ustawień w czasie wykonywania w języku C#</span><span class="sxs-lookup"><span data-stu-id="b222a-105">To Read Settings at Run Time with C#</span></span>  
  
-   <span data-ttu-id="b222a-106">Dostęp za pośrednictwem elementu członkowskiego Properties.Settings.Default odpowiednie ustawienia.</span><span class="sxs-lookup"><span data-stu-id="b222a-106">Access the appropriate setting via the Properties.Settings.Default member.</span></span> <span data-ttu-id="b222a-107">Poniższy przykład przedstawia sposób przypisać ustawienie o nazwie `myColor` właściwości BackColor.</span><span class="sxs-lookup"><span data-stu-id="b222a-107">The following example shows how to assign a setting named `myColor` to a BackColor property.</span></span> <span data-ttu-id="b222a-108">Użytkownik musi mieć wcześniej utworzony plik ustawień zawierający ustawienie o nazwie `myColor` typu `System.Drawing.Color`.</span><span class="sxs-lookup"><span data-stu-id="b222a-108">It requires you to have previously created a Settings file containing a setting named `myColor` of type `System.Drawing.Color`.</span></span> <span data-ttu-id="b222a-109">Aby uzyskać informacje dotyczące tworzenia pliku ustawień, zobacz [jak: utworzyć nowe ustawienie w czasie projektowania](../../../../docs/framework/winforms/advanced/how-to-create-a-new-setting-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="b222a-109">For information about creating a Settings file, see [How To: Create a New Setting at Design Time](../../../../docs/framework/winforms/advanced/how-to-create-a-new-setting-at-design-time.md).</span></span>  
  
    ```  
    // C#  
    this.BackColor = Properties.Settings.Default.myColor;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="b222a-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b222a-110">See Also</span></span>  
 [<span data-ttu-id="b222a-111">Używanie ustawień aplikacji i ustawień użytkownika</span><span class="sxs-lookup"><span data-stu-id="b222a-111">Using Application Settings and User Settings</span></span>](../../../../docs/framework/winforms/advanced/using-application-settings-and-user-settings.md)  
 [<span data-ttu-id="b222a-112">Instrukcje: pisanie ustawień użytkownika w czasie wykonywania w języku C#</span><span class="sxs-lookup"><span data-stu-id="b222a-112">How To: Write User Settings at Run Time with C#</span></span>](../../../../docs/framework/winforms/advanced/how-to-write-user-settings-at-run-time-with-csharp.md)  
 [<span data-ttu-id="b222a-113">Przegląd ustawień aplikacji</span><span class="sxs-lookup"><span data-stu-id="b222a-113">Application Settings Overview</span></span>](../../../../docs/framework/winforms/advanced/application-settings-overview.md)
