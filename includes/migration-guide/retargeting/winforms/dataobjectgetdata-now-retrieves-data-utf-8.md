---
ms.openlocfilehash: 3f330d5e601d599231ef0336b785e677fe1d114e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616081"
---
### <a name="dataobjectgetdata-now-retrieves-data-as-utf-8"></a><span data-ttu-id="8f8bb-101">Obiekt DataObject. GetData teraz pobiera dane jako UTF-8</span><span class="sxs-lookup"><span data-stu-id="8f8bb-101">DataObject.GetData now retrieves data as UTF-8</span></span>

#### <a name="details"></a><span data-ttu-id="8f8bb-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="8f8bb-102">Details</span></span>

<span data-ttu-id="8f8bb-103">W przypadku aplikacji przeznaczonych dla .NET Framework 4 lub uruchomionych w .NET Framework 4.5.1 lub wcześniejszych wersjach program `DataObject.GetData` Pobiera dane sformatowane w formacie HTML jako ciąg ASCII.</span><span class="sxs-lookup"><span data-stu-id="8f8bb-103">For apps that target the .NET Framework 4 or that run on the .NET Framework 4.5.1 or earlier versions, `DataObject.GetData` retrieves HTML-formatted data as an ASCII string.</span></span> <span data-ttu-id="8f8bb-104">W związku z tym znaki inne niż ASCII (znaki, których kody ASCII są większe niż 0x7F) są reprezentowane przez dwa znaki losowe.</span><span class="sxs-lookup"><span data-stu-id="8f8bb-104">As a result, non-ASCII characters (characters whose ASCII codes are greater than 0x7F) are represented by two random characters.</span></span><p/><span data-ttu-id="8f8bb-105">W przypadku aplikacji przeznaczonych dla .NET Framework 4,5 lub nowszych i uruchamianych na .NET Framework 4.5.2 `DataObject.GetData` Pobiera dane sformatowane w formacie HTML jako UTF-8, które reprezentują znaki większe niż 0x7F poprawnie.</span><span class="sxs-lookup"><span data-stu-id="8f8bb-105">For apps that target the .NET Framework 4.5 or later and run on the .NET Framework 4.5.2, `DataObject.GetData` retrieves HTML-formatted data as UTF-8, which represents characters greater than 0x7F correctly.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="8f8bb-106">Sugestia</span><span class="sxs-lookup"><span data-stu-id="8f8bb-106">Suggestion</span></span>

<span data-ttu-id="8f8bb-107">Jeśli zaimplementowano obejście problemu z kodowaniem w postaci ciągów sformatowanych w formacie HTML (na przykład przez jawne kodowanie ciągu HTML pobranego ze schowka przez przekazanie go do <xref:System.Text.UTF8Encoding.GetString(System.Byte[],System.Int32,System.Int32)?displayProperty=fullName> ) i przekierowanie aplikacji z wersji 4 do 4,5, należy usunąć obejście. Jeśli z jakiegoś powodu jest konieczne stare zachowanie, aplikacja może kierować do .NET Framework 4,0, aby uzyskać takie zachowanie.</span><span class="sxs-lookup"><span data-stu-id="8f8bb-107">If you implemented a workaround for the encoding problem with HTML-formatted strings (for example, by explicitly encoding the HTML string retrieved from the Clipboard by passing it to <xref:System.Text.UTF8Encoding.GetString(System.Byte[],System.Int32,System.Int32)?displayProperty=fullName>) and you're retargeting your app from version 4 to 4.5, that workaround should be removed.If the old behavior is needed for some reason, the app can target the .NET Framework 4.0 to get that behavior.</span></span>

| <span data-ttu-id="8f8bb-108">Nazwa</span><span class="sxs-lookup"><span data-stu-id="8f8bb-108">Name</span></span>    | <span data-ttu-id="8f8bb-109">Wartość</span><span class="sxs-lookup"><span data-stu-id="8f8bb-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="8f8bb-110">Zakres</span><span class="sxs-lookup"><span data-stu-id="8f8bb-110">Scope</span></span>   | <span data-ttu-id="8f8bb-111">Brzeg</span><span class="sxs-lookup"><span data-stu-id="8f8bb-111">Edge</span></span>        |
| <span data-ttu-id="8f8bb-112">Wersja</span><span class="sxs-lookup"><span data-stu-id="8f8bb-112">Version</span></span> | <span data-ttu-id="8f8bb-113">4.5.2</span><span class="sxs-lookup"><span data-stu-id="8f8bb-113">4.5.2</span></span>       |
| <span data-ttu-id="8f8bb-114">Typ</span><span class="sxs-lookup"><span data-stu-id="8f8bb-114">Type</span></span>    | <span data-ttu-id="8f8bb-115">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="8f8bb-115">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="8f8bb-116">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="8f8bb-116">Affected APIs</span></span>

- <xref:System.Windows.DataObject.GetData(System.String)?displayProperty=nameWithType>
- <xref:System.Windows.DataObject.GetData(System.Type)?displayProperty=nameWithType>
- <xref:System.Windows.DataObject.GetData(System.String,System.Boolean)?displayProperty=nameWithType>
