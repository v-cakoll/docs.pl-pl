---
ms.openlocfilehash: e66a5c2a33a4ab5cf35013c1843936ffd01f90a2
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614747"
---
### <a name="serialport-background-thread-exceptions"></a><span data-ttu-id="6c8e8-101">Wyjątki wątku w tle klasy SerialPort</span><span class="sxs-lookup"><span data-stu-id="6c8e8-101">SerialPort background thread exceptions</span></span>

#### <a name="details"></a><span data-ttu-id="6c8e8-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="6c8e8-102">Details</span></span>

<span data-ttu-id="6c8e8-103">Wątki w tle utworzone za pomocą <xref:System.IO.Ports.SerialPort> strumieni nie przerywają procesu, gdy są zgłaszane wyjątki systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="6c8e8-103">Background threads created with <xref:System.IO.Ports.SerialPort> streams no longer terminate the process when OS exceptions are thrown.</span></span> <br/><span data-ttu-id="6c8e8-104">W aplikacjach, które są przeznaczone dla .NET Framework 4,7 i wcześniejszych wersji, proces zostaje zakończony, gdy w wątku w tle utworzonym za pomocą strumienia zostanie zgłoszony wyjątek systemu operacyjnego <xref:System.IO.Ports.SerialPort> .</span><span class="sxs-lookup"><span data-stu-id="6c8e8-104">In applications that target the .NET Framework 4.7 and earlier versions, a process is terminated when an operating system exception is thrown on a background thread created with a <xref:System.IO.Ports.SerialPort> stream.</span></span> <br/><span data-ttu-id="6c8e8-105">W aplikacjach przeznaczonych dla .NET Framework 4.7.1 lub nowszej wersji wątki w tle czekają na zdarzenia systemu operacyjnego związane z aktywnym portem szeregowym i mogą ulec awarii w niektórych przypadkach, takich jak nagłe usunięcie portu szeregowego.</span><span class="sxs-lookup"><span data-stu-id="6c8e8-105">In applications that target the .NET Framework 4.7.1 or a later version, background threads wait for OS events related to the active serial port and could crash in some cases, such as sudden removal of the serial port.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="6c8e8-106">Sugestia</span><span class="sxs-lookup"><span data-stu-id="6c8e8-106">Suggestion</span></span>

<span data-ttu-id="6c8e8-107">W przypadku aplikacji przeznaczonych dla .NET Framework 4.7.1 można zrezygnować z obsługi wyjątków, jeśli nie jest to pożądane, dodając następujący element do `<runtime>` sekcji `app.config` pliku:</span><span class="sxs-lookup"><span data-stu-id="6c8e8-107">For apps that target the .NET Framework 4.7.1, you can opt out of the exception handling if it is not desirable by adding the following to the `<runtime>` section of your `app.config` file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.IO.Ports.DoNotCatchSerialStreamThreadExceptions=true" />
</runtime>
```

<span data-ttu-id="6c8e8-108">W przypadku aplikacji przeznaczonych dla wcześniejszych wersji .NET Framework ale uruchamianych na .NET Framework 4.7.1 lub nowszych można zrezygnować z obsługi wyjątków, dodając następujący element do `<runtime>` sekcji `app.config` pliku:</span><span class="sxs-lookup"><span data-stu-id="6c8e8-108">For apps that target earlier versions of the .NET Framework but run on the .NET Framework 4.7.1 or later, you can opt in to the exception handling by adding the following to the `<runtime>` section of your `app.config` file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.IO.Ports.DoNotCatchSerialStreamThreadExceptions=false" />
</runtime>
```

| <span data-ttu-id="6c8e8-109">Nazwa</span><span class="sxs-lookup"><span data-stu-id="6c8e8-109">Name</span></span>    | <span data-ttu-id="6c8e8-110">Wartość</span><span class="sxs-lookup"><span data-stu-id="6c8e8-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="6c8e8-111">Zakres</span><span class="sxs-lookup"><span data-stu-id="6c8e8-111">Scope</span></span>   | <span data-ttu-id="6c8e8-112">Mały</span><span class="sxs-lookup"><span data-stu-id="6c8e8-112">Minor</span></span>       |
| <span data-ttu-id="6c8e8-113">Wersja</span><span class="sxs-lookup"><span data-stu-id="6c8e8-113">Version</span></span> | <span data-ttu-id="6c8e8-114">4.7.1</span><span class="sxs-lookup"><span data-stu-id="6c8e8-114">4.7.1</span></span>       |
| <span data-ttu-id="6c8e8-115">Typ</span><span class="sxs-lookup"><span data-stu-id="6c8e8-115">Type</span></span>    | <span data-ttu-id="6c8e8-116">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="6c8e8-116">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="6c8e8-117">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="6c8e8-117">Affected APIs</span></span>

- <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>
