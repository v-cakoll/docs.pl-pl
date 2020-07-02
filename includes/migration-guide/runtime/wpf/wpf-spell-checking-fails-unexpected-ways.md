---
ms.openlocfilehash: d4f0095bc9fde98087dce528c8154d9c9ac6ddb7
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621839"
---
### <a name="wpf-spell-checking-fails-in-unexpected-ways"></a><span data-ttu-id="ca816-101">Sprawdzanie pisowni WPF kończy się niepowodzeniem na nieoczekiwany sposób</span><span class="sxs-lookup"><span data-stu-id="ca816-101">WPF Spell Checking fails in unexpected ways</span></span>

#### <a name="details"></a><span data-ttu-id="ca816-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="ca816-102">Details</span></span>

<span data-ttu-id="ca816-103">Obejmuje to wiele problemów z modułem sprawdzania pisowni WPF:</span><span class="sxs-lookup"><span data-stu-id="ca816-103">This includes a number of WPF Spell Checker issues:</span></span><ul><li><span data-ttu-id="ca816-104">Moduł sprawdzania pisowni WPF czasami zgłasza<xref:System.Runtime.InteropServices.COMException?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="ca816-104">WPF Spell Checker sometimes throws <xref:System.Runtime.InteropServices.COMException?displayProperty=fullName></span></span></li><li><span data-ttu-id="ca816-105">Sprawdzanie pisowni WPF kończy się niepowodzeniem, <xref:System.UnauthorizedAccessException> gdy aplikacje są uruchamiane za pomocą polecenia "Uruchom jako inny użytkownik"</span><span class="sxs-lookup"><span data-stu-id="ca816-105">WPF Spell Checker fails with <xref:System.UnauthorizedAccessException> when applications are launched using 'run as different user'</span></span></li><li><span data-ttu-id="ca816-106">Moduł sprawdzania pisowni WPF nieprawidłowo identyfikuje błędy pisowni w wyrazach złożonych, takich jak "Hausnummer" w języku niemieckim.</span><span class="sxs-lookup"><span data-stu-id="ca816-106">WPF Spell Checker incorrectly identifies spelling errors in compound words like 'Hausnummer' in German.</span></span></li></ul>

#### <a name="suggestion"></a><span data-ttu-id="ca816-107">Sugestia</span><span class="sxs-lookup"><span data-stu-id="ca816-107">Suggestion</span></span>

<span data-ttu-id="ca816-108">Problem #1 — ten problem został rozwiązany w programie .NET Framework 4.6.2 #2 — funkcja sprawdzania pisowni WPF nie jest już obsługiwana, gdy aplikacje są uruchamiane za pomocą polecenia "Uruchom jako inny użytkownik".</span><span class="sxs-lookup"><span data-stu-id="ca816-108">Issue #1 - This has been fixed in .NET Framework 4.6.2 Issue #2 - WPF Spell Checker is no longer supported when applications are launched using 'run as different user'.</span></span> <span data-ttu-id="ca816-109">Uruchamianie .NET Framework 4.6.2, aplikacje uruchomione w ten sposób nie przestaną działać w sposób nieoczekiwany — zamiast tego sprawdzanie pisowni zostanie wyłączone w trybie dyskretnym.</span><span class="sxs-lookup"><span data-stu-id="ca816-109">Starting .NET Framework 4.6.2, applications launched in this manner will no longer crash unexpectedly - instead the Spell Checker will be silently disabled.</span></span> <span data-ttu-id="ca816-110">#3 problemu — ten problem został rozwiązany w .NET Framework 4.6.2.</span><span class="sxs-lookup"><span data-stu-id="ca816-110">Issue #3 - This has been fixed in .NET Framework 4.6.2.</span></span>

| <span data-ttu-id="ca816-111">Nazwa</span><span class="sxs-lookup"><span data-stu-id="ca816-111">Name</span></span>    | <span data-ttu-id="ca816-112">Wartość</span><span class="sxs-lookup"><span data-stu-id="ca816-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="ca816-113">Zakres</span><span class="sxs-lookup"><span data-stu-id="ca816-113">Scope</span></span>   |<span data-ttu-id="ca816-114">Brzeg</span><span class="sxs-lookup"><span data-stu-id="ca816-114">Edge</span></span>|
|<span data-ttu-id="ca816-115">Wersja</span><span class="sxs-lookup"><span data-stu-id="ca816-115">Version</span></span>|<span data-ttu-id="ca816-116">4.6.1</span><span class="sxs-lookup"><span data-stu-id="ca816-116">4.6.1</span></span>|
|<span data-ttu-id="ca816-117">Typ</span><span class="sxs-lookup"><span data-stu-id="ca816-117">Type</span></span>|<span data-ttu-id="ca816-118">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="ca816-118">Runtime</span></span>|
