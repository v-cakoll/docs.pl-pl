---
ms.openlocfilehash: 47d0aa554d88726caca35fa6bebe4d863fdc0695
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235432"
---
### <a name="eventsourcewriteevent-impls-must-pass-writeevent-the-same-parameters-that-it-received-plus-id"></a><span data-ttu-id="ed133-101">EventSource.WriteEvent impls należy przekazać WriteEvent tych samych parametrów, które otrzymał (plus identyfikator)</span><span class="sxs-lookup"><span data-stu-id="ed133-101">EventSource.WriteEvent impls must pass WriteEvent the same parameters that it received (plus ID)</span></span>

|   |   |
|---|---|
|<span data-ttu-id="ed133-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="ed133-102">Details</span></span>|<span data-ttu-id="ed133-103">Środowisko wykonawcze wymusza teraz kontraktu, który określa następujące czynności: Klasa pochodząca z <xref:System.Diagnostics.Tracing.EventSource?displayProperty=name> definiujący ETW metody zdarzeń należy wywołać klasy bazowej <code>EventSource.WriteEvent</code> metody z Identyfikatorem zdarzenia następuje te same argumenty, które metody zdarzeń ETW został przekazany.</span><span class="sxs-lookup"><span data-stu-id="ed133-103">The runtime now enforces the contract that specifies the following: A class derived from <xref:System.Diagnostics.Tracing.EventSource?displayProperty=name> that defines an ETW event method must call the base class <code>EventSource.WriteEvent</code> method with the event ID followed by the same arguments that the ETW event method was passed.</span></span>|
|<span data-ttu-id="ed133-104">Sugestia</span><span class="sxs-lookup"><span data-stu-id="ed133-104">Suggestion</span></span>|<span data-ttu-id="ed133-105"><xref:System.IndexOutOfRangeException?displayProperty=name> Wyjątek jest generowany, jeśli <xref:System.Diagnostics.Tracing.EventListener?displayProperty=name> odczytuje <xref:System.Diagnostics.Tracing.EventSource?displayProperty=name> danych w procesie dla źródła zdarzenia, który narusza aktualne niniejszej Umowy.</span><span class="sxs-lookup"><span data-stu-id="ed133-105">An <xref:System.IndexOutOfRangeException?displayProperty=name> exception is thrown if an <xref:System.Diagnostics.Tracing.EventListener?displayProperty=name> reads <xref:System.Diagnostics.Tracing.EventSource?displayProperty=name> data in process for an event source that violates this contract.</span></span>|
|<span data-ttu-id="ed133-106">Zakres</span><span class="sxs-lookup"><span data-stu-id="ed133-106">Scope</span></span>|<span data-ttu-id="ed133-107">Mały</span><span class="sxs-lookup"><span data-stu-id="ed133-107">Minor</span></span>|
|<span data-ttu-id="ed133-108">Wersja</span><span class="sxs-lookup"><span data-stu-id="ed133-108">Version</span></span>|<span data-ttu-id="ed133-109">4.5.1</span><span class="sxs-lookup"><span data-stu-id="ed133-109">4.5.1</span></span>|
|<span data-ttu-id="ed133-110">Typ</span><span class="sxs-lookup"><span data-stu-id="ed133-110">Type</span></span>|<span data-ttu-id="ed133-111">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="ed133-111">Runtime</span></span>|
