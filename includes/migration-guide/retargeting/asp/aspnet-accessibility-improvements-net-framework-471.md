---
ms.openlocfilehash: 418bcdca1e9a325894891d7b0e080ce035e2d1b4
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614682"
---
### <a name="aspnet-accessibility-improvements-in-net-framework-471"></a><span data-ttu-id="7c72b-101">Udoskonalenia ułatwień dostępu ASP.NET w programie .NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="7c72b-101">ASP.NET Accessibility Improvements in .NET Framework 4.7.1</span></span>

#### <a name="details"></a><span data-ttu-id="7c72b-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="7c72b-102">Details</span></span>

<span data-ttu-id="7c72b-103">Począwszy od .NET Framework 4.7.1, ASP.NET ulepszono sposób, w jaki formanty sieci Web ASP.NET współpracują z technologią ułatwień dostępu w programie Visual Studio, aby lepiej obsługiwać klientów ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="7c72b-103">Starting with the .NET Framework 4.7.1, ASP.NET has improved how ASP.NET Web Controls work with accessibility technology in Visual Studio to better support ASP.NET customers.</span></span>  <span data-ttu-id="7c72b-104">Należą do nich następujące zmiany:</span><span class="sxs-lookup"><span data-stu-id="7c72b-104">These include the following changes:</span></span>

- <span data-ttu-id="7c72b-105">Zmiany w celu zaimplementowania brakujących wzorców dostępności interfejsu użytkownika w kontrolkach, takich jak okno dialogowe Dodawanie pola w Kreatorze widoku szczegółów lub okno dialogowe Konfiguruj widok ListView kreatora ListView.</span><span class="sxs-lookup"><span data-stu-id="7c72b-105">Changes to implement missing UI accessibility patterns in controls, like the Add Field dialog in the Details View wizard, or the Configure ListView dialog of the ListView wizard.</span></span>
- <span data-ttu-id="7c72b-106">Zmiany w celu usprawnienia wyświetlania w trybie duży kontrast, takie jak edytor pól modułu stronicowania danych.</span><span class="sxs-lookup"><span data-stu-id="7c72b-106">Changes to improve the display in High Contrast mode, like the Data Pager Fields Editor.</span></span>
- <span data-ttu-id="7c72b-107">Zmiany w celu ulepszenia środowiska nawigacji klawiatury dla kontrolek, takich jak okno dialogowe pola w Kreatorze Edytuj pola modułu stronicowania kontrolki formantu DataPager, okno dialogowe Konfigurowanie obiektu ObjectContext lub okno dialogowe Konfigurowanie wyboru danych Kreatora konfiguracji źródła danych.</span><span class="sxs-lookup"><span data-stu-id="7c72b-107">Changes to improve the keyboard navigation experiences for controls, like the Fields dialog in the Edit Pager Fields wizard of the DataPager control, the Configure ObjectContext dialog, or the Configure Data Selection dialog of the Configure Data Source wizard.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="7c72b-108">Sugestia</span><span class="sxs-lookup"><span data-stu-id="7c72b-108">Suggestion</span></span>

<span data-ttu-id="7c72b-109">**Jak wybrać lub wycofać te zmiany** Aby projektant programu Visual Studio mógł korzystać z tych zmian, musi on działać na .NET Framework 4.7.1 lub nowszym.</span><span class="sxs-lookup"><span data-stu-id="7c72b-109">**How to opt in or out of these changes** In order for the Visual Studio Designer to benefit from these changes, it must run on the .NET Framework 4.7.1 or later.</span></span> <span data-ttu-id="7c72b-110">Aplikacja sieci Web może korzystać z tych zmian w jeden z następujących sposobów:</span><span class="sxs-lookup"><span data-stu-id="7c72b-110">The web application can benefit from these changes in either of the following ways:</span></span>

- <span data-ttu-id="7c72b-111">Zainstaluj program Visual Studio 2017 15,3 lub nowszy, który obsługuje nowe funkcje ułatwień dostępu domyślnie z następującym przełącznikiem AppContext.</span><span class="sxs-lookup"><span data-stu-id="7c72b-111">Install Visual Studio 2017 15.3 or later, which supports the new accessibility features with the following AppContext Switch by default.</span></span>
- <span data-ttu-id="7c72b-112">Zrezygnuj ze starszych zachowań ułatwień dostępu, dodając `Switch.UseLegacyAccessibilityFeatures` przełącznik AppContext do `<runtime>` sekcji w pliku devenv.exe.config i ustawiając go na `false` , jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="7c72b-112">Opt out of the legacy accessibility behaviors by adding the `Switch.UseLegacyAccessibilityFeatures` AppContext switch to the `<runtime>` section in the devenv.exe.config file and setting it to `false`, as the following example shows.</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
<runtime>
...
<!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true/false;key2=true/false'  -->
<AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false" />
...
</runtime>
</configuration>
```

<span data-ttu-id="7c72b-113">Aplikacje, które są przeznaczone dla .NET Framework 4.7.1 lub nowszych i chcą zachować starsze zachowanie ułatwień dostępu, mogą zrezygnować z używania starszych funkcji ułatwień dostępu przez jawne ustawienie tego przełącznika AppContext na `true` .</span><span class="sxs-lookup"><span data-stu-id="7c72b-113">Applications that target the .NET Framework 4.7.1 or later and want to preserve the legacy accessibility behavior can opt in to the use of legacy accessibility features by explicitly setting this AppContext switch to `true`.</span></span>

| <span data-ttu-id="7c72b-114">Nazwa</span><span class="sxs-lookup"><span data-stu-id="7c72b-114">Name</span></span>    | <span data-ttu-id="7c72b-115">Wartość</span><span class="sxs-lookup"><span data-stu-id="7c72b-115">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="7c72b-116">Zakres</span><span class="sxs-lookup"><span data-stu-id="7c72b-116">Scope</span></span>   | <span data-ttu-id="7c72b-117">Mały</span><span class="sxs-lookup"><span data-stu-id="7c72b-117">Minor</span></span>       |
| <span data-ttu-id="7c72b-118">Wersja</span><span class="sxs-lookup"><span data-stu-id="7c72b-118">Version</span></span> | <span data-ttu-id="7c72b-119">4.7.1</span><span class="sxs-lookup"><span data-stu-id="7c72b-119">4.7.1</span></span>       |
| <span data-ttu-id="7c72b-120">Typ</span><span class="sxs-lookup"><span data-stu-id="7c72b-120">Type</span></span>    | <span data-ttu-id="7c72b-121">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="7c72b-121">Retargeting</span></span> |
