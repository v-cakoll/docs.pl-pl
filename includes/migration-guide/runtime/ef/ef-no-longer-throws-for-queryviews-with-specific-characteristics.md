---
ms.openlocfilehash: c6c897c13c84ce4b2be21da18e5702365518f286
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620327"
---
### <a name="ef-no-longer-throws-for-queryviews-with-specific-characteristics"></a><span data-ttu-id="7911a-101">EF nie zgłasza już) obiektów QueryView o określonych cechach</span><span class="sxs-lookup"><span data-stu-id="7911a-101">EF no longer throws for QueryViews with specific characteristics</span></span>

#### <a name="details"></a><span data-ttu-id="7911a-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="7911a-102">Details</span></span>

<span data-ttu-id="7911a-103">Entity Framework już nie zgłasza <xref:System.StackOverflowException?displayProperty=fullName> wyjątku, gdy aplikacja wykonuje zapytanie, które obejmuje QueryView z właściwością nawigacji 0.. 1, która próbuje dołączyć powiązane jednostki jako część zapytania.</span><span class="sxs-lookup"><span data-stu-id="7911a-103">Entity Framework no longer throws a <xref:System.StackOverflowException?displayProperty=fullName> exception when an app executes a query that involves a QueryView with a 0..1 navigation property that attempts to include the related entities as part of the query.</span></span> <span data-ttu-id="7911a-104">Na przykład przez wywołanie metody <code>.Include(e =&gt; e.RelatedNavProp)</code> .</span><span class="sxs-lookup"><span data-stu-id="7911a-104">For example, by calling <code>.Include(e =&gt; e.RelatedNavProp)</code>.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="7911a-105">Sugestia</span><span class="sxs-lookup"><span data-stu-id="7911a-105">Suggestion</span></span>

<span data-ttu-id="7911a-106">Ta zmiana ma wpływ tylko na kod, który używa) obiektów QueryView z 1-0.. 1 relacji podczas wykonywania zapytań wywoływanych przez program. Być.</span><span class="sxs-lookup"><span data-stu-id="7911a-106">This change only affects code that uses QueryViews with 1-0..1 relationships when running queries that call .Include.</span></span> <span data-ttu-id="7911a-107">Zwiększa niezawodność i powinien być przejrzysty dla niemal wszystkich aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7911a-107">It improves reliability and should be transparent to almost all apps.</span></span> <span data-ttu-id="7911a-108">Jeśli jednak spowoduje to nieoczekiwane zachowanie, można je wyłączyć, dodając następujący wpis do <code>&lt;appSettings&gt;</code> sekcji w pliku konfiguracji aplikacji:</span><span class="sxs-lookup"><span data-stu-id="7911a-108">However, if it causes unexpected behavior, you can disable it by adding the following entry to the <code>&lt;appSettings&gt;</code> section of the app's configuration file:</span></span><pre><code class="lang-xml">&lt;add key=&quot;EntityFramework_SimplifyUserSpecifiedViews&quot; value=&quot;false&quot; /&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="7911a-109">Nazwa</span><span class="sxs-lookup"><span data-stu-id="7911a-109">Name</span></span>    | <span data-ttu-id="7911a-110">Wartość</span><span class="sxs-lookup"><span data-stu-id="7911a-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="7911a-111">Zakres</span><span class="sxs-lookup"><span data-stu-id="7911a-111">Scope</span></span>   |<span data-ttu-id="7911a-112">Brzeg</span><span class="sxs-lookup"><span data-stu-id="7911a-112">Edge</span></span>|
|<span data-ttu-id="7911a-113">Wersja</span><span class="sxs-lookup"><span data-stu-id="7911a-113">Version</span></span>|<span data-ttu-id="7911a-114">4.5.2</span><span class="sxs-lookup"><span data-stu-id="7911a-114">4.5.2</span></span>|
|<span data-ttu-id="7911a-115">Typ</span><span class="sxs-lookup"><span data-stu-id="7911a-115">Type</span></span>|<span data-ttu-id="7911a-116">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="7911a-116">Runtime</span></span>|
