---
ms.openlocfilehash: 1329a86db4227f75dfba7c50bbbdc2fc23099528
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620278"
---
### <a name="sqlbulkcopy-uses-destination-column-encoding-for-strings"></a><span data-ttu-id="6cef4-101">SqlBulkCopy używa kodowania kolumn docelowych dla ciągów</span><span class="sxs-lookup"><span data-stu-id="6cef4-101">SqlBulkCopy uses destination column encoding for strings</span></span>

#### <a name="details"></a><span data-ttu-id="6cef4-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="6cef4-102">Details</span></span>

<span data-ttu-id="6cef4-103">Podczas wstawiania danych do kolumny program <xref:System.Data.SqlClient.SqlBulkCopy?displayProperty=fullName> używa kodowania kolumny docelowej zamiast domyślnego kodowania dla <code>VARCHAR</code> <code>CHAR</code> typów i.</span><span class="sxs-lookup"><span data-stu-id="6cef4-103">When inserting data into a column, <xref:System.Data.SqlClient.SqlBulkCopy?displayProperty=fullName> uses the encoding of the destination column rather than the default encoding for <code>VARCHAR</code> and <code>CHAR</code> types.</span></span> <span data-ttu-id="6cef4-104">Ta zmiana eliminuje możliwość uszkodzenia danych na skutek użycia domyślnego kodowania w sytuacji, gdy w kolumnie docelowej nie jest używane kodowanie domyślne.</span><span class="sxs-lookup"><span data-stu-id="6cef4-104">This change eliminates the possibility of data corruption caused by using the default encoding when the destination column does not use the default encoding.</span></span> <span data-ttu-id="6cef4-105">W rzadkich przypadkach istniejąca aplikacja może zgłosić wyjątek SqlException, jeśli zmiana kodowania powoduje, że dane są zbyt duże, aby mieściły się w kolumnie docelowej.</span><span class="sxs-lookup"><span data-stu-id="6cef4-105">In rare cases, an existing application may throw a SqlException exception if the change in encoding produces data that is too big to fit into the destination column.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="6cef4-106">Sugestia</span><span class="sxs-lookup"><span data-stu-id="6cef4-106">Suggestion</span></span>

<span data-ttu-id="6cef4-107">Należy oczekiwać, że <xref:System.Data.SqlClient.SqlBulkCopy?displayProperty=fullName> dane nie będą już uszkodzone z powodu różnic między kodowaniem.</span><span class="sxs-lookup"><span data-stu-id="6cef4-107">Expect that <xref:System.Data.SqlClient.SqlBulkCopy?displayProperty=fullName> will no longer corrupt data due to encoding differences.</span></span> <span data-ttu-id="6cef4-108">Jeśli są kopiowane ciągi bliskie rozmiaru kolumny docelowej, może być konieczne przeprowadzenie wstępnej kodowania danych (do skopiowania w celu sprawdzenia, czy dane zmieszczą się w kolumnie docelowej), czy do przechwycenia <xref:System.Data.SqlClient.SqlException?displayProperty=fullName> .</span><span class="sxs-lookup"><span data-stu-id="6cef4-108">If strings near the destination column's size limit are being copied, it may be necessary to either pre-encode data (to be copied to check that the data will fit in the destination column) or catch <xref:System.Data.SqlClient.SqlException?displayProperty=fullName>s.</span></span>

| <span data-ttu-id="6cef4-109">Nazwa</span><span class="sxs-lookup"><span data-stu-id="6cef4-109">Name</span></span>    | <span data-ttu-id="6cef4-110">Wartość</span><span class="sxs-lookup"><span data-stu-id="6cef4-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="6cef4-111">Zakres</span><span class="sxs-lookup"><span data-stu-id="6cef4-111">Scope</span></span>   |<span data-ttu-id="6cef4-112">Brzeg</span><span class="sxs-lookup"><span data-stu-id="6cef4-112">Edge</span></span>|
|<span data-ttu-id="6cef4-113">Wersja</span><span class="sxs-lookup"><span data-stu-id="6cef4-113">Version</span></span>|<span data-ttu-id="6cef4-114">4.5</span><span class="sxs-lookup"><span data-stu-id="6cef4-114">4.5</span></span>|
|<span data-ttu-id="6cef4-115">Typ</span><span class="sxs-lookup"><span data-stu-id="6cef4-115">Type</span></span>|<span data-ttu-id="6cef4-116">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="6cef4-116">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="6cef4-117">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="6cef4-117">Affected APIs</span></span>

-<xref:System.Data.SqlClient.SqlBulkCopy?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlBulkCopy.%23ctor(System.Data.SqlClient.SqlConnection)></li></ul>|
