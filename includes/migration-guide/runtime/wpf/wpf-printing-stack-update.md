---
ms.openlocfilehash: e613f0c52c77efebf250f5935d5cbfc29bc09a6b
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2019
ms.locfileid: "67802539"
---
### <a name="wpf-printing-stack-update"></a><span data-ttu-id="c84e8-101">Aktualizację stosu drukowanie WPF</span><span class="sxs-lookup"><span data-stu-id="c84e8-101">WPF Printing Stack Update</span></span>

|   |   |
|---|---|
|<span data-ttu-id="c84e8-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="c84e8-102">Details</span></span>|<span data-ttu-id="c84e8-103">Za pomocą drukowanie interfejsów API firmy WPF <xref:System.Printing.PrintQueue?displayProperty=name> teraz wywołania interfejsu API pakietu dokument Drukuj okna na rzecz teraz przestarzałe API drukowanie plików XPS.</span><span class="sxs-lookup"><span data-stu-id="c84e8-103">WPF's Printing APIs using <xref:System.Printing.PrintQueue?displayProperty=name> now call Window's Print Document Package API in favor of the now deprecated XPS Print API.</span></span> <span data-ttu-id="c84e8-104">Zmiana została wprowadzona przy użyciu użytkowanie pamiętać; Użytkownicy ani deweloperzy nie powinny zostać wyświetlone wszelkie zmiany w zachowanie lub użycie interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="c84e8-104">The change was made with serviceability in mind; neither users nor developers should see any changes in behavior or API usage.</span></span> <span data-ttu-id="c84e8-105">Nowy stos drukowania jest domyślnie włączona, podczas uruchamiania w systemie Windows 10 Creators Update.</span><span class="sxs-lookup"><span data-stu-id="c84e8-105">The new printing stack is enabled by default when running in Windows 10 Creators Update.</span></span> <span data-ttu-id="c84e8-106">Stary stosu drukowania będą nadal działać tak jak wcześniej w starszych wersjach Windows.</span><span class="sxs-lookup"><span data-stu-id="c84e8-106">The old printing stack will still continue to work just as before in older Windows versions.</span></span>|
|<span data-ttu-id="c84e8-107">Sugestia</span><span class="sxs-lookup"><span data-stu-id="c84e8-107">Suggestion</span></span>|<span data-ttu-id="c84e8-108">Aby użyć starego stosu w aktualizacji systemu Windows 10 dla twórców, ustaw <code>UseXpsOMPrinting</code> wartości REG_DWORD <code>HKEY_CURRENT_USER\Software\Microsoft\.NETFramework\Windows Presentation Foundation\Printing</code> klucza rejestru w celu <code>1</code>.</span><span class="sxs-lookup"><span data-stu-id="c84e8-108">To use the old stack in Windows 10 Creators Update, set the <code>UseXpsOMPrinting</code> REG_DWORD value of the <code>HKEY_CURRENT_USER\Software\Microsoft\.NETFramework\Windows Presentation Foundation\Printing</code> registry key to <code>1</code>.</span></span>|
|<span data-ttu-id="c84e8-109">Scope</span><span class="sxs-lookup"><span data-stu-id="c84e8-109">Scope</span></span>|<span data-ttu-id="c84e8-110">Krawędź</span><span class="sxs-lookup"><span data-stu-id="c84e8-110">Edge</span></span>|
|<span data-ttu-id="c84e8-111">Wersja</span><span class="sxs-lookup"><span data-stu-id="c84e8-111">Version</span></span>|<span data-ttu-id="c84e8-112">4.7</span><span class="sxs-lookup"><span data-stu-id="c84e8-112">4.7</span></span>|
|<span data-ttu-id="c84e8-113">Typ</span><span class="sxs-lookup"><span data-stu-id="c84e8-113">Type</span></span>|<span data-ttu-id="c84e8-114">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="c84e8-114">Runtime</span></span>|

