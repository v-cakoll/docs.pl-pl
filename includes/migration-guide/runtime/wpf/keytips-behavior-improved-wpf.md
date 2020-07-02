---
ms.openlocfilehash: 9659068304eb208fd6a0a753273453bc669fbc56
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621274"
---
### <a name="keytips-behavior-improved-in-wpf"></a><span data-ttu-id="2c170-101">Ulepszone zachowanie podpowiedzi w WPF</span><span class="sxs-lookup"><span data-stu-id="2c170-101">Keytips behavior improved in WPF</span></span>

#### <a name="details"></a><span data-ttu-id="2c170-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="2c170-102">Details</span></span>

<span data-ttu-id="2c170-103">W celu zachowania zgodności z zachowaniem programu Microsoft Word i Eksploratora Windows należy zmodyfikować zachowanie podpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="2c170-103">Keytips behavior has been modified to bring parity with behavior on Microsoft Word and Windows Explorer.</span></span> <span data-ttu-id="2c170-104">Sprawdzając, czy stan poradę dotyczącą klawiszy jest włączony lub nie jest w przypadku <xref:System.Windows.Input.KeyEventArgs.SystemKey> naciśnięcia (w szczególności <xref:System.Windows.Input.Key> lub <xref:System.Windows.Input.Key.F11> ), WPF odpowiednio obsługuje klucze poradę dotyczącą klawiszy.</span><span class="sxs-lookup"><span data-stu-id="2c170-104">By checking whether keytip state is enabled or not in the case of a <xref:System.Windows.Input.KeyEventArgs.SystemKey> (in particular, <xref:System.Windows.Input.Key> or <xref:System.Windows.Input.Key.F11>) being pressed, WPF handles keytip keys appropriately.</span></span> <span data-ttu-id="2c170-105">Porady dotyczące klawisza umożliwiają teraz odrzucanie menu nawet wtedy, gdy jest ono otwierane za pomocą myszy.</span><span class="sxs-lookup"><span data-stu-id="2c170-105">Keytips now dismiss a menu even when it is opened by mouse.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="2c170-106">Sugestia</span><span class="sxs-lookup"><span data-stu-id="2c170-106">Suggestion</span></span>

<span data-ttu-id="2c170-107">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="2c170-107">N/A</span></span>

| <span data-ttu-id="2c170-108">Nazwa</span><span class="sxs-lookup"><span data-stu-id="2c170-108">Name</span></span>    | <span data-ttu-id="2c170-109">Wartość</span><span class="sxs-lookup"><span data-stu-id="2c170-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="2c170-110">Zakres</span><span class="sxs-lookup"><span data-stu-id="2c170-110">Scope</span></span>   |<span data-ttu-id="2c170-111">Brzeg</span><span class="sxs-lookup"><span data-stu-id="2c170-111">Edge</span></span>|
|<span data-ttu-id="2c170-112">Wersja</span><span class="sxs-lookup"><span data-stu-id="2c170-112">Version</span></span>|<span data-ttu-id="2c170-113">4.7.2</span><span class="sxs-lookup"><span data-stu-id="2c170-113">4.7.2</span></span>|
|<span data-ttu-id="2c170-114">Typ</span><span class="sxs-lookup"><span data-stu-id="2c170-114">Type</span></span>|<span data-ttu-id="2c170-115">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="2c170-115">Runtime</span></span>|
