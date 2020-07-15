---
ms.openlocfilehash: 9f6703c77e17ac9376aee944b891f4635dc7632e
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/14/2020
ms.locfileid: "86309161"
---
### <a name="winforms-methods-now-throw-argumentexception"></a><span data-ttu-id="8d82a-101">Metody WinForms teraz generują ArgumentException</span><span class="sxs-lookup"><span data-stu-id="8d82a-101">WinForms methods now throw ArgumentException</span></span>

<span data-ttu-id="8d82a-102">Niektóre metody Windows Forms teraz generują <xref:System.ArgumentException> dla nieprawidłowych argumentów, w których wcześniej nie zostały.</span><span class="sxs-lookup"><span data-stu-id="8d82a-102">Some Windows Forms methods now throw an <xref:System.ArgumentException> for invalid arguments, where previously they did not.</span></span>

#### <a name="change-description"></a><span data-ttu-id="8d82a-103">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="8d82a-103">Change description</span></span>

<span data-ttu-id="8d82a-104">Wcześniej przekazywanie argumentów nieoczekiwanego lub nieprawidłowego typu do określonych metod Windows Forms spowoduje nieokreślony stan.</span><span class="sxs-lookup"><span data-stu-id="8d82a-104">Previously, passing arguments of an unexpected or incorrect type to certain Windows Forms methods would result in an indeterminate state.</span></span> <span data-ttu-id="8d82a-105">Począwszy od platformy .NET 5,0, metody te generują teraz, <xref:System.ArgumentException> gdy przekazane nieprawidłowe argumenty.</span><span class="sxs-lookup"><span data-stu-id="8d82a-105">Starting in .NET 5.0, these methods now throw an <xref:System.ArgumentException> when passed invalid arguments.</span></span>

<span data-ttu-id="8d82a-106">Zgłaszanie jest <xref:System.ArgumentException> zgodne z zachowaniem środowiska uruchomieniowego .NET.</span><span class="sxs-lookup"><span data-stu-id="8d82a-106">Throwing an <xref:System.ArgumentException> conforms to the behavior of the .NET runtime.</span></span> <span data-ttu-id="8d82a-107">Usprawnia to również środowisko debugowania, przez co jasno komunikuje się, który argument jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="8d82a-107">It also improves the debugging experience by clearly communicating which argument is invalid.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="8d82a-108">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="8d82a-108">Version introduced</span></span>

<span data-ttu-id="8d82a-109">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="8d82a-109">.NET 5.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="8d82a-110">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="8d82a-110">Recommended action</span></span>

- <span data-ttu-id="8d82a-111">Zaktualizuj kod, aby zapobiec przekazywaniu nieprawidłowych argumentów.</span><span class="sxs-lookup"><span data-stu-id="8d82a-111">Update the code to prevent passing invalid arguments.</span></span>
- <span data-ttu-id="8d82a-112">W razie potrzeby dojście do <xref:System.ArgumentException> wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="8d82a-112">If necessary, handle an <xref:System.ArgumentException> when calling the method.</span></span>

#### <a name="category"></a><span data-ttu-id="8d82a-113">Kategoria</span><span class="sxs-lookup"><span data-stu-id="8d82a-113">Category</span></span>

<span data-ttu-id="8d82a-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8d82a-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="8d82a-115">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="8d82a-115">Affected APIs</span></span>

<span data-ttu-id="8d82a-116">Poniższa tabela zawiera listę odpowiednich metod i parametrów:</span><span class="sxs-lookup"><span data-stu-id="8d82a-116">The following table lists the affected methods and parameters:</span></span>

| <span data-ttu-id="8d82a-117">Metoda</span><span class="sxs-lookup"><span data-stu-id="8d82a-117">Method</span></span> | <span data-ttu-id="8d82a-118">Nazwa parametru</span><span class="sxs-lookup"><span data-stu-id="8d82a-118">Parameter name</span></span> | <span data-ttu-id="8d82a-119">Warunek</span><span class="sxs-lookup"><span data-stu-id="8d82a-119">Condition</span></span> | <span data-ttu-id="8d82a-120">Dodana wersja</span><span class="sxs-lookup"><span data-stu-id="8d82a-120">Version added</span></span> |
|-|-|-|-|
| <xref:System.Windows.Forms.TabControl.GetToolTipText(System.Object)?displayProperty=fullName> | `item` | <span data-ttu-id="8d82a-121">Argument nie jest typu <xref:System.Windows.Forms.TabPage> .</span><span class="sxs-lookup"><span data-stu-id="8d82a-121">Argument is not of type <xref:System.Windows.Forms.TabPage>.</span></span> | <span data-ttu-id="8d82a-122">Wersja zapoznawcza 1</span><span class="sxs-lookup"><span data-stu-id="8d82a-122">Preview 1</span></span> |
| <xref:System.Windows.Forms.DataFormats.GetFormat(System.String)?displayProperty=fullName> | `format` | <span data-ttu-id="8d82a-123">Argument to `null` , <xref:System.String.Empty?displayProperty=nameWithType> lub biały znak.</span><span class="sxs-lookup"><span data-stu-id="8d82a-123">Argument is `null`, <xref:System.String.Empty?displayProperty=nameWithType>, or white space.</span></span> | <span data-ttu-id="8d82a-124">Wersja zapoznawcza 5</span><span class="sxs-lookup"><span data-stu-id="8d82a-124">Preview 5</span></span> |
| <xref:System.Windows.Forms.InputLanguageChangedEventArgs.%23ctor(System.Globalization.CultureInfo,System.Byte)> | `culture` | <span data-ttu-id="8d82a-125">Nie można pobrać elementu `InputLanguage` dla określonej kultury.</span><span class="sxs-lookup"><span data-stu-id="8d82a-125">Unable to retrieve an `InputLanguage` for the specified culture.</span></span> | <span data-ttu-id="8d82a-126">Wersja zapoznawcza 7</span><span class="sxs-lookup"><span data-stu-id="8d82a-126">Preview 7</span></span> |

<!-- 

#### Affected APIs

- `M:System.Windows.Forms.TabControl.GetToolTipText(System.Object)`
- `M:System.Windows.Forms.DataFormats.GetFormat(System.String)`
- `M:System.Windows.Forms.InputLanguageChangedEventArgs.%23ctor(System.Globalization.CultureInfo,System.Byte)`

-->
