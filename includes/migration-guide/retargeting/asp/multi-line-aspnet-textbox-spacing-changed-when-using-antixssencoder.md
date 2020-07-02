---
ms.openlocfilehash: 150b98255b3075a8fe8cad60ce234206b788a5f5
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617183"
---
### <a name="multi-line-aspnet-textbox-spacing-changed-when-using-antixssencoder"></a><span data-ttu-id="1992f-101">W wielowierszowym polu tekstowym ASP.Net TextBox zmieniły się odstępy w przypadku użycia klasy AntiXSSEncoder</span><span class="sxs-lookup"><span data-stu-id="1992f-101">Multi-line ASP.Net TextBox spacing changed when using AntiXSSEncoder</span></span>

#### <a name="details"></a><span data-ttu-id="1992f-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="1992f-102">Details</span></span>

<span data-ttu-id="1992f-103">W programie .NET Framework 4.0 dodatkowe wiersze były wstawiane między wierszami wielowierszowego pola tekstowego podczas ogłaszania zwrotnego w przypadku użycia klasy <xref:System.Web.Security.AntiXss.AntiXssEncoder?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="1992f-103">In .NET Framework 4.0, extra lines were inserted between lines of a multi-line text box on postback, if using the <xref:System.Web.Security.AntiXss.AntiXssEncoder?displayProperty=fullName>.</span></span> <span data-ttu-id="1992f-104">W wersji .NET Framework 4.5 te dodatkowe podziały wiersza nie są uwzględnione, ale tylko wtedy, gdy platformą docelową aplikacji internetowej jest program .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="1992f-104">In .NET Framework 4.5, those extra line breaks are not included, but only if the web app is targeting .NET Framework 4.5</span></span>

#### <a name="suggestion"></a><span data-ttu-id="1992f-105">Sugestia</span><span class="sxs-lookup"><span data-stu-id="1992f-105">Suggestion</span></span>

<span data-ttu-id="1992f-106">Należy pamiętać, że w aplikacjach sieci Web w wersji 4.0 przekierowanych na platformę .NET Framework 4.5 może wystąpić ulepszenie wielowierszowych pól tekstowych polegające na tym, że nie będą już wstawiane dodatkowe podziały wiersza.</span><span class="sxs-lookup"><span data-stu-id="1992f-106">Be aware that 4.0 web apps retargeted to .NET Framework 4.5 may have multi-line text boxes improved to no longer insert extra line breaks.</span></span> <span data-ttu-id="1992f-107">Jeśli nie jest to pożądane, aplikacja może przejawiać stare zachowanie podczas uruchamiania na platformie .NET Framework 4.5, o ile zostanie przekierowana do programu .NET Framework 4.0.</span><span class="sxs-lookup"><span data-stu-id="1992f-107">If this is not desirable, the app  can have the old behavior when running on .NET Framework 4.5 by targeting the .NET Framework 4.0.</span></span>

| <span data-ttu-id="1992f-108">Nazwa</span><span class="sxs-lookup"><span data-stu-id="1992f-108">Name</span></span>    | <span data-ttu-id="1992f-109">Wartość</span><span class="sxs-lookup"><span data-stu-id="1992f-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="1992f-110">Zakres</span><span class="sxs-lookup"><span data-stu-id="1992f-110">Scope</span></span>   | <span data-ttu-id="1992f-111">Mały</span><span class="sxs-lookup"><span data-stu-id="1992f-111">Minor</span></span>       |
| <span data-ttu-id="1992f-112">Wersja</span><span class="sxs-lookup"><span data-stu-id="1992f-112">Version</span></span> | <span data-ttu-id="1992f-113">4.5</span><span class="sxs-lookup"><span data-stu-id="1992f-113">4.5</span></span>         |
| <span data-ttu-id="1992f-114">Typ</span><span class="sxs-lookup"><span data-stu-id="1992f-114">Type</span></span>    | <span data-ttu-id="1992f-115">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="1992f-115">Retargeting</span></span> |
