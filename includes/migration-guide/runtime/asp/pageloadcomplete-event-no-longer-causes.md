---
ms.openlocfilehash: 39d609c955596354d1af28b4ed19d367dab0462b
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620158"
---
### <a name="pageloadcomplete-event-no-longer-causes-systemwebuiwebcontrolsentitydatasource-control-to-invoke-data-binding"></a><span data-ttu-id="d548e-101">Zdarzenie Page. LoadComplete nie powoduje już wystąpienia elementu System. Web. UI. WebControls. kontrolka EntityDataSource do wywołania powiązania danych</span><span class="sxs-lookup"><span data-stu-id="d548e-101">Page.LoadComplete event no longer causes System.Web.UI.WebControls.EntityDataSource control to invoke data binding</span></span>

#### <a name="details"></a><span data-ttu-id="d548e-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="d548e-102">Details</span></span>

<span data-ttu-id="d548e-103"><xref:System.Web.UI.Page.LoadComplete>Zdarzenie nie powoduje już <xref:System.Web.UI.WebControls.EntityDataSource?displayProperty=fullName> wywołania powiązania danych dla zmian w celu tworzenia/aktualizowania/usuwania parametrów.</span><span class="sxs-lookup"><span data-stu-id="d548e-103">The <xref:System.Web.UI.Page.LoadComplete> event no longer causes the <xref:System.Web.UI.WebControls.EntityDataSource?displayProperty=fullName> control to invoke data binding for changes to create/update/delete parameters.</span></span> <span data-ttu-id="d548e-104">Ta zmiana eliminuje niezależną podróż do bazy danych, zapobiega resetowaniu wartości formantów oraz tworzy zachowanie zgodne z innymi kontrolkami danych, takimi jak <xref:System.Web.UI.WebControls.SqlDataSource?displayProperty=fullName> i <xref:System.Web.UI.WebControls.ObjectDataSource?displayProperty=fullName> .</span><span class="sxs-lookup"><span data-stu-id="d548e-104">This change eliminates an extraneous trip to the database, prevents the values of controls from being reset, and produces behavior that is consistent with other data controls, such as <xref:System.Web.UI.WebControls.SqlDataSource?displayProperty=fullName> and <xref:System.Web.UI.WebControls.ObjectDataSource?displayProperty=fullName>.</span></span> <span data-ttu-id="d548e-105">Ta zmiana powoduje inne zachowanie w przypadku, gdy aplikacje są zależne od wywołującego powiązania danych w <xref:System.Web.UI.Page.LoadComplete> zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="d548e-105">This change produces different behavior in the unlikely event that applications rely on invoking data binding in the <xref:System.Web.UI.Page.LoadComplete> event.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="d548e-106">Sugestia</span><span class="sxs-lookup"><span data-stu-id="d548e-106">Suggestion</span></span>

<span data-ttu-id="d548e-107">Jeśli istnieje potrzeba wiązania z danymi, ręcznie Wywołaj wywołanie metody wywołania zwrotnego w zdarzeniu, które jest wcześniej wykonywane po zakończeniu.</span><span class="sxs-lookup"><span data-stu-id="d548e-107">If there is a need for databinding, manually invoke databind in an event that is earlier in the post-back.</span></span>

| <span data-ttu-id="d548e-108">Nazwa</span><span class="sxs-lookup"><span data-stu-id="d548e-108">Name</span></span>    | <span data-ttu-id="d548e-109">Wartość</span><span class="sxs-lookup"><span data-stu-id="d548e-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="d548e-110">Zakres</span><span class="sxs-lookup"><span data-stu-id="d548e-110">Scope</span></span>   |<span data-ttu-id="d548e-111">Brzeg</span><span class="sxs-lookup"><span data-stu-id="d548e-111">Edge</span></span>|
|<span data-ttu-id="d548e-112">Wersja</span><span class="sxs-lookup"><span data-stu-id="d548e-112">Version</span></span>|<span data-ttu-id="d548e-113">4.5</span><span class="sxs-lookup"><span data-stu-id="d548e-113">4.5</span></span>|
|<span data-ttu-id="d548e-114">Typ</span><span class="sxs-lookup"><span data-stu-id="d548e-114">Type</span></span>|<span data-ttu-id="d548e-115">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="d548e-115">Runtime</span></span>|
