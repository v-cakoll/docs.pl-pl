---
ms.openlocfilehash: f6fd75c5b49156f44d31c650ea452eb549f13b0e
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901743"
---
### <a name="mvc-jsonresult-moved-to-microsoftaspnetcoremvccore"></a><span data-ttu-id="6f7b0-101">MVC: JsonResult przeniesiony do Microsoft. AspNetCore. MVC. Core</span><span class="sxs-lookup"><span data-stu-id="6f7b0-101">MVC: JsonResult moved to Microsoft.AspNetCore.Mvc.Core</span></span>

<span data-ttu-id="6f7b0-102">`JsonResult` przeniesiono do zestawu `Microsoft.AspNetCore.Mvc.Core`.</span><span class="sxs-lookup"><span data-stu-id="6f7b0-102">`JsonResult` has moved to the `Microsoft.AspNetCore.Mvc.Core` assembly.</span></span> <span data-ttu-id="6f7b0-103">Ten typ jest używany do zdefiniowania w pliku [Microsoft. AspNetCore. MVC. formatującegos. JSON](https://www.nuget.org/packages/Microsoft.AspNetCore.Mvc.Formatters.Json).</span><span class="sxs-lookup"><span data-stu-id="6f7b0-103">This type used to be defined in [Microsoft.AspNetCore.Mvc.Formatters.Json](https://www.nuget.org/packages/Microsoft.AspNetCore.Mvc.Formatters.Json).</span></span> <span data-ttu-id="6f7b0-104">Atrybut na poziomie zestawu [[TypeForwardedTo]](xref:System.Runtime.CompilerServices.TypeForwardedToAttribute) został dodany do `Microsoft.AspNetCore.Mvc.Formatters.Json`, aby rozwiązać ten problem w przypadku większości użytkowników.</span><span class="sxs-lookup"><span data-stu-id="6f7b0-104">An assembly-level [[TypeForwardedTo]](xref:System.Runtime.CompilerServices.TypeForwardedToAttribute) attribute was added to `Microsoft.AspNetCore.Mvc.Formatters.Json` to address this issue for the majority of users.</span></span> <span data-ttu-id="6f7b0-105">Aplikacje korzystające z bibliotek innych firm mogą napotkać problemy.</span><span class="sxs-lookup"><span data-stu-id="6f7b0-105">Apps that use third-party libraries may encounter issues.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="6f7b0-106">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="6f7b0-106">Version introduced</span></span>

<span data-ttu-id="6f7b0-107">3,0 wersja zapoznawcza 6</span><span class="sxs-lookup"><span data-stu-id="6f7b0-107">3.0 Preview 6</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="6f7b0-108">Stare zachowanie</span><span class="sxs-lookup"><span data-stu-id="6f7b0-108">Old behavior</span></span>

<span data-ttu-id="6f7b0-109">Aplikacja używająca pomyślnie utworzonych bibliotek opartych na 2,2.</span><span class="sxs-lookup"><span data-stu-id="6f7b0-109">An app using a 2.2-based library builds successfully.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="6f7b0-110">Nowe zachowanie</span><span class="sxs-lookup"><span data-stu-id="6f7b0-110">New behavior</span></span>

<span data-ttu-id="6f7b0-111">Kompilacja nie powiedzie się w aplikacji korzystającej z biblioteki opartej na 2,2.</span><span class="sxs-lookup"><span data-stu-id="6f7b0-111">An app using a 2.2-based library fails compilation.</span></span> <span data-ttu-id="6f7b0-112">Wystąpił błąd zawierający odmianę następującego tekstu:</span><span class="sxs-lookup"><span data-stu-id="6f7b0-112">An error containing a variation of the following text is provided:</span></span>

```
The type 'JsonResult' exists in both 'Microsoft.AspNetCore.Mvc.Core, Version=3.0.0.0, Culture=neutral, PublicKeyToken=adb9793829ddae60' and 'Microsoft.AspNetCore.Mvc.Formatters.Json, Version=2.0.0.0, Culture=neutral, PublicKeyToken=adb9793829ddae60'
```

<span data-ttu-id="6f7b0-113">Przykład takiego problemu można znaleźć w temacie [dotnet/aspnetcore # 7220](https://github.com/dotnet/aspnetcore/issues/7220).</span><span class="sxs-lookup"><span data-stu-id="6f7b0-113">For an example of such an issue, see [dotnet/aspnetcore#7220](https://github.com/dotnet/aspnetcore/issues/7220).</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="6f7b0-114">Przyczyna zmiany</span><span class="sxs-lookup"><span data-stu-id="6f7b0-114">Reason for change</span></span>

<span data-ttu-id="6f7b0-115">Zmiany na poziomie platformy do kompozycji ASP.NET Core zgodnie z opisem w polu [ASPNET/anonse # 325](https://github.com/aspnet/Announcements/issues/325).</span><span class="sxs-lookup"><span data-stu-id="6f7b0-115">Platform-level changes to the composition of ASP.NET Core as described at [aspnet/Announcements#325](https://github.com/aspnet/Announcements/issues/325).</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="6f7b0-116">Zalecane działanie</span><span class="sxs-lookup"><span data-stu-id="6f7b0-116">Recommended action</span></span>

<span data-ttu-id="6f7b0-117">Biblioteki skompilowane pod kątem 2,2 wersji `Microsoft.AspNetCore.Mvc.Formatters.Json` mogą wymagać ponownego skompilowania w celu rozwiązania problemu dla wszystkich klientów.</span><span class="sxs-lookup"><span data-stu-id="6f7b0-117">Libraries compiled against the 2.2 version of `Microsoft.AspNetCore.Mvc.Formatters.Json` may need to recompile to address the problem for all consumers.</span></span> <span data-ttu-id="6f7b0-118">Jeśli to dotyczy, skontaktuj się z autorem biblioteki.</span><span class="sxs-lookup"><span data-stu-id="6f7b0-118">If affected, contact the library author.</span></span> <span data-ttu-id="6f7b0-119">Poproś o ponowną kompilację biblioteki do celu ASP.NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="6f7b0-119">Request recompilation of the library to target ASP.NET Core 3.0.</span></span>

#### <a name="category"></a><span data-ttu-id="6f7b0-120">Kategoria</span><span class="sxs-lookup"><span data-stu-id="6f7b0-120">Category</span></span>

<span data-ttu-id="6f7b0-121">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="6f7b0-121">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="6f7b0-122">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="6f7b0-122">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Mvc.JsonResult?displayProperty=nameWithType>

<!-- 

### Affected APIs

`T:Microsoft.AspNetCore.Mvc.JsonResult`

-->
