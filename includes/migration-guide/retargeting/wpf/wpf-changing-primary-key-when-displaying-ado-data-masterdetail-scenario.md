---
ms.openlocfilehash: 35fc4782ebbba33f5fc6668712af9d89d00cafe9
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614973"
---
### <a name="wpf-changing-a-primary-key-when-displaying-ado-data-in-a-masterdetail-scenario"></a><span data-ttu-id="77542-101">WPF zmiana klucza podstawowego podczas wyświetlania danych ADO w scenariuszu głównym/szczegółowym</span><span class="sxs-lookup"><span data-stu-id="77542-101">WPF Changing a primary key when displaying ADO data in a Master/Detail scenario</span></span>

#### <a name="details"></a><span data-ttu-id="77542-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="77542-102">Details</span></span>

<span data-ttu-id="77542-103">Załóżmy, że istnieje kolekcja ADO elementów typu `Order` , z relacją o nazwie OrderDetails, &quot; &quot; która odnosi się do kolekcji elementów typu `Detail` za pośrednictwem klucza podstawowego &quot; IDZamówienia &quot; .</span><span class="sxs-lookup"><span data-stu-id="77542-103">Suppose you have an ADO collection of items of type `Order`, with a relation named &quot;OrderDetails&quot; relating it to a collection of items of type `Detail` via the primary key &quot;OrderID&quot;.</span></span> <span data-ttu-id="77542-104">W aplikacji WPF można powiązać formant listy z danymi szczegółowymi dotyczącymi danej kolejności:</span><span class="sxs-lookup"><span data-stu-id="77542-104">In your WPF app, you can bind a list control to the details for a given order:</span></span>

```xaml
<ListBox ItemsSource="{Binding Path=OrderDetails}" >
```

<span data-ttu-id="77542-105">gdzie DataContext jest `Order` .</span><span class="sxs-lookup"><span data-stu-id="77542-105">where the DataContext is an `Order`.</span></span> <span data-ttu-id="77542-106">WPF Pobiera wartość `OrderDetails` właściwości-kolekcji D wszystkich `Detail` elementów, które `OrderID` pasują do `OrderID` elementu głównego.</span><span class="sxs-lookup"><span data-stu-id="77542-106">WPF gets the value of the `OrderDetails` property - a collection D of all the `Detail` items whose `OrderID` matches the `OrderID` of the master item.</span></span> <span data-ttu-id="77542-107">Zmiana klucza podstawowego elementu głównego jest zachowaniem `OrderID` .</span><span class="sxs-lookup"><span data-stu-id="77542-107">The behavior change arises when you change the primary key `OrderID` of the master item.</span></span> <span data-ttu-id="77542-108">Obiekt ADO automatycznie zmienia `OrderID` każdy z rekordów, których dotyczy ten rekord w kolekcji szczegóły (a mianowicie skopiowane do kolekcji D).</span><span class="sxs-lookup"><span data-stu-id="77542-108">ADO automatically changes the `OrderID` of each of the affected records in the Details collection (namely the ones copied into collection D).</span></span>  <span data-ttu-id="77542-109">Ale co się dzieje z D?</span><span class="sxs-lookup"><span data-stu-id="77542-109">But what happens to D?</span></span>

- <span data-ttu-id="77542-110">Stare zachowanie: Kolekcja D została wyczyszczona.</span><span class="sxs-lookup"><span data-stu-id="77542-110">Old behavior: Collection D is cleared.</span></span> <span data-ttu-id="77542-111">Element główny *nie zgłasza powiadomienia* o zmianie dla właściwości `OrderDetails` .</span><span class="sxs-lookup"><span data-stu-id="77542-111">The master item does *not* raise a change notification for property `OrderDetails`.</span></span> <span data-ttu-id="77542-112">Element ListBox nadal używa kolekcji D, która jest teraz pusta.</span><span class="sxs-lookup"><span data-stu-id="77542-112">The ListBox continues to use collection D, which is now empty.</span></span>
- <span data-ttu-id="77542-113">Nowe zachowanie: Kolekcja D nie została zmieniona.</span><span class="sxs-lookup"><span data-stu-id="77542-113">New behavior:  Collection D is unchanged.</span></span> <span data-ttu-id="77542-114">Każdy z elementów zgłasza powiadomienie o zmianie dla `OrderID` właściwości.</span><span class="sxs-lookup"><span data-stu-id="77542-114">Each of its items raises a change notification for the `OrderID` property.</span></span> <span data-ttu-id="77542-115">Element ListBox nadal używa kolekcji D i wyświetla szczegóły z nowym `OrderID` .</span><span class="sxs-lookup"><span data-stu-id="77542-115">The ListBox continues to use collection D, and displays the details with the new `OrderID`.</span></span> <span data-ttu-id="77542-116">WPF implementuje nowe zachowanie przez utworzenie kolekcji D w inny sposób: przez wywołanie metody ADO <xref:System.Data.DataRowView.CreateChildView(System.Data.DataRelation,System.Boolean)?displayProperty=nameWithType> z `followParent` argumentem ustawionym na `true` .</span><span class="sxs-lookup"><span data-stu-id="77542-116">WPF implements the new behavior by creating collection D in a different way:  by calling the ADO method <xref:System.Data.DataRowView.CreateChildView(System.Data.DataRelation,System.Boolean)?displayProperty=nameWithType> with the `followParent` argument set to `true`.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="77542-117">Sugestia</span><span class="sxs-lookup"><span data-stu-id="77542-117">Suggestion</span></span>

<span data-ttu-id="77542-118">Aplikacja pobiera nowe zachowanie przy użyciu następującego przełącznika AppContext.</span><span class="sxs-lookup"><span data-stu-id="77542-118">An app gets the new behavior by using the following AppContext switch.</span></span>

```xml
<configuration>
  <runtime>
    <AppContextSwitchOverrides value="Switch.System.Windows.Data.DoNotUseFollowParentWhenBindingToADODataRelation=false"/>
  </runtime>
</configuration>
```

<span data-ttu-id="77542-119">Ustawienie domyślne przełącznika `true` (stare zachowanie) dla aplikacji przeznaczonych dla platformy .NET 4.7.1 lub nowszych oraz do `false` (nowe zachowanie) dla aplikacji przeznaczonych dla platformy .NET 4.7.2 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="77542-119">The switch defaults to `true` (old behavior) for apps that target .NET 4.7.1 or below, and to `false` (new behavior) for apps that target .NET 4.7.2 or above.</span></span>

| <span data-ttu-id="77542-120">Nazwa</span><span class="sxs-lookup"><span data-stu-id="77542-120">Name</span></span>    | <span data-ttu-id="77542-121">Wartość</span><span class="sxs-lookup"><span data-stu-id="77542-121">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="77542-122">Zakres</span><span class="sxs-lookup"><span data-stu-id="77542-122">Scope</span></span>   | <span data-ttu-id="77542-123">Mały</span><span class="sxs-lookup"><span data-stu-id="77542-123">Minor</span></span>       |
| <span data-ttu-id="77542-124">Wersja</span><span class="sxs-lookup"><span data-stu-id="77542-124">Version</span></span> | <span data-ttu-id="77542-125">4.7.2</span><span class="sxs-lookup"><span data-stu-id="77542-125">4.7.2</span></span>       |
| <span data-ttu-id="77542-126">Typ</span><span class="sxs-lookup"><span data-stu-id="77542-126">Type</span></span>    | <span data-ttu-id="77542-127">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="77542-127">Retargeting</span></span> |
