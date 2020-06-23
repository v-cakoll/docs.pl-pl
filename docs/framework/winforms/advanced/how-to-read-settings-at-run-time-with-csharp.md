---
title: 'Porady: czytanie ustawień w czasie wykonywania w języku C#'
description: Informacje o sposobie odczytywania ustawień zakresu aplikacji i zakresu użytkownika w czasie wykonywania w języku C# za pomocą obiektu Properties.
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], reading
- application settings [Windows Forms], run time
- application settings [Windows Forms], C#
ms.assetid: dbe8bf09-5e1c-49da-9192-154033d7240b
ms.openlocfilehash: d784544e018bb693c501e35ea36fcae1946ef5eb
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/17/2020
ms.locfileid: "84903357"
---
# <a name="how-to-read-settings-at-run-time-with-c"></a><span data-ttu-id="44844-103">Instrukcje: odczytywanie ustawień w czasie wykonywania przy użyciu języka C\#</span><span class="sxs-lookup"><span data-stu-id="44844-103">How To: Read Settings at Run Time With C\#</span></span>

<span data-ttu-id="44844-104">W czasie wykonywania za pomocą obiektu Properties można odczytać zarówno ustawienia zakresu aplikacji, jak i zakresu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="44844-104">You can read both Application-scoped and User-scoped settings at run time via the Properties object.</span></span> <span data-ttu-id="44844-105">Obiekt właściwości uwidacznia wszystkie ustawienia domyślne projektu za pośrednictwem właściwości. Settings. Default w domyślnej przestrzeni nazw projektu, w którym są zdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="44844-105">The Properties object exposes all of the default settings for the project via the Properties.Settings.Default member in the default namespace of the project they are defined in.</span></span>  
  
## <a name="to-read-settings-at-run-time-with-c"></a><span data-ttu-id="44844-106">Aby odczytać ustawienia w czasie wykonywania przy użyciu języka C\#</span><span class="sxs-lookup"><span data-stu-id="44844-106">To Read Settings at Run Time with C\#</span></span>
  
<span data-ttu-id="44844-107">Uzyskaj dostęp do odpowiedniego ustawienia za pośrednictwem właściwości. Settings. default.</span><span class="sxs-lookup"><span data-stu-id="44844-107">Access the appropriate setting via the Properties.Settings.Default member.</span></span> <span data-ttu-id="44844-108">Poniższy przykład pokazuje, jak przypisać ustawienia o nazwie `myColor` do właściwości BackColor.</span><span class="sxs-lookup"><span data-stu-id="44844-108">The following example shows how to assign a setting named `myColor` to a BackColor property.</span></span> <span data-ttu-id="44844-109">Wymaga wcześniej utworzenia pliku ustawień zawierającego ustawienie o nazwie `myColor` typu `System.Drawing.Color` .</span><span class="sxs-lookup"><span data-stu-id="44844-109">It requires you to have previously created a Settings file containing a setting named `myColor` of type `System.Drawing.Color`.</span></span> <span data-ttu-id="44844-110">Aby uzyskać informacje na temat tworzenia pliku ustawień, zobacz [How to: Create a New Setting in Time Design](how-to-create-a-new-setting-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="44844-110">For information about creating a Settings file, see [How To: Create a New Setting at Design Time](how-to-create-a-new-setting-at-design-time.md).</span></span>  
  
```csharp
this.BackColor = Properties.Settings.Default.myColor;  
```  
  
## <a name="see-also"></a><span data-ttu-id="44844-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="44844-111">See also</span></span>

- [<span data-ttu-id="44844-112">Używanie ustawień aplikacji i ustawień użytkownika</span><span class="sxs-lookup"><span data-stu-id="44844-112">Using Application Settings and User Settings</span></span>](using-application-settings-and-user-settings.md)
- [<span data-ttu-id="44844-113">Instrukcje: pisanie ustawień użytkownika w czasie wykonywania w języku C#</span><span class="sxs-lookup"><span data-stu-id="44844-113">How To: Write User Settings at Run Time with C#</span></span>](how-to-write-user-settings-at-run-time-with-csharp.md)
- [<span data-ttu-id="44844-114">Przegląd ustawień aplikacji</span><span class="sxs-lookup"><span data-stu-id="44844-114">Application Settings Overview</span></span>](application-settings-overview.md)
