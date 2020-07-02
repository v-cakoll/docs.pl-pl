---
ms.openlocfilehash: 5e2e8d1ec5d698d1c1649c2a0a1b4b77dbdf4022
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621277"
---
### <a name="wpf-printing-stack-update"></a><span data-ttu-id="d568d-101">Aktualizacja stosu drukowania WPF</span><span class="sxs-lookup"><span data-stu-id="d568d-101">WPF Printing Stack Update</span></span>

#### <a name="details"></a><span data-ttu-id="d568d-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="d568d-102">Details</span></span>

<span data-ttu-id="d568d-103">Interfejsy API drukowania platformy WPF korzystające z <xref:System.Printing.PrintQueue?displayProperty=fullName> interfejsu API Wywołaj teraz okna wywołującego na rzecz obecnie przestarzałego interfejsu API drukowania XPS.</span><span class="sxs-lookup"><span data-stu-id="d568d-103">WPF's Printing APIs using <xref:System.Printing.PrintQueue?displayProperty=fullName> now call Window's Print Document Package API in favor of the now deprecated XPS Print API.</span></span> <span data-ttu-id="d568d-104">Zmiany zostały wprowadzone z myślą o potrzebach. ani użytkownicy, ani deweloperzy nie powinni widzieć żadnych zmian w zachowaniu lub użyciu interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="d568d-104">The change was made with serviceability in mind; neither users nor developers should see any changes in behavior or API usage.</span></span> <span data-ttu-id="d568d-105">Nowy stos drukowania jest domyślnie włączony podczas uruchamiania aktualizacji systemu Windows 10 dla twórców.</span><span class="sxs-lookup"><span data-stu-id="d568d-105">The new printing stack is enabled by default when running in Windows 10 Creators Update.</span></span> <span data-ttu-id="d568d-106">Stary stos drukowania nadal będzie działać tak samo jak wcześniej w starszych wersjach systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="d568d-106">The old printing stack will still continue to work just as before in older Windows versions.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="d568d-107">Sugestia</span><span class="sxs-lookup"><span data-stu-id="d568d-107">Suggestion</span></span>

<span data-ttu-id="d568d-108">Aby użyć starego stosu w aktualizacji systemu Windows 10 dla twórców, należy ustawić <code>UseXpsOMPrinting</code> wartość REG_DWORD <code>HKEY_CURRENT_USER\Software\Microsoft\.NETFramework\Windows Presentation Foundation\Printing</code> klucza rejestru na <code>1</code> .</span><span class="sxs-lookup"><span data-stu-id="d568d-108">To use the old stack in Windows 10 Creators Update, set the <code>UseXpsOMPrinting</code> REG_DWORD value of the <code>HKEY_CURRENT_USER\Software\Microsoft\.NETFramework\Windows Presentation Foundation\Printing</code> registry key to <code>1</code>.</span></span>

| <span data-ttu-id="d568d-109">Nazwa</span><span class="sxs-lookup"><span data-stu-id="d568d-109">Name</span></span>    | <span data-ttu-id="d568d-110">Wartość</span><span class="sxs-lookup"><span data-stu-id="d568d-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="d568d-111">Zakres</span><span class="sxs-lookup"><span data-stu-id="d568d-111">Scope</span></span>   |<span data-ttu-id="d568d-112">Brzeg</span><span class="sxs-lookup"><span data-stu-id="d568d-112">Edge</span></span>|
|<span data-ttu-id="d568d-113">Wersja</span><span class="sxs-lookup"><span data-stu-id="d568d-113">Version</span></span>|<span data-ttu-id="d568d-114">4,7</span><span class="sxs-lookup"><span data-stu-id="d568d-114">4.7</span></span>|
|<span data-ttu-id="d568d-115">Typ</span><span class="sxs-lookup"><span data-stu-id="d568d-115">Type</span></span>|<span data-ttu-id="d568d-116">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="d568d-116">Runtime</span></span>|
