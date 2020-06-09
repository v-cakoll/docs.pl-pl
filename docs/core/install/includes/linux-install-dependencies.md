---
ms.openlocfilehash: b371525c9f4e57c6a09e5bb9232884e5c5e707e0
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84603007"
---

<span data-ttu-id="2182a-101">Po zainstalowaniu programu przy użyciu Menedżera pakietów te biblioteki są instalowane dla Ciebie.</span><span class="sxs-lookup"><span data-stu-id="2182a-101">When you install with a package manager, these libraries are installed for you.</span></span> <span data-ttu-id="2182a-102">Jeśli jednak ręcznie zainstalujesz platformę .NET Core lub opublikujesz aplikację, musisz upewnić się, że te biblioteki są zainstalowane:</span><span class="sxs-lookup"><span data-stu-id="2182a-102">But, if you manually install .NET Core or you publish a self-contained app, you'll need to make sure these libraries are installed:</span></span>

- <span data-ttu-id="2182a-103">LTTng — zespół sklepu uniwersalnego</span><span class="sxs-lookup"><span data-stu-id="2182a-103">lttng-ust</span></span>
- <span data-ttu-id="2182a-104">libcurl</span><span class="sxs-lookup"><span data-stu-id="2182a-104">libcurl</span></span>
- <span data-ttu-id="2182a-105">OpenSSL — libs</span><span class="sxs-lookup"><span data-stu-id="2182a-105">openssl-libs</span></span>
- <span data-ttu-id="2182a-106">krb5 — libs</span><span class="sxs-lookup"><span data-stu-id="2182a-106">krb5-libs</span></span>
- <span data-ttu-id="2182a-107">libicu</span><span class="sxs-lookup"><span data-stu-id="2182a-107">libicu</span></span>
- <span data-ttu-id="2182a-108">zlib</span><span class="sxs-lookup"><span data-stu-id="2182a-108">zlib</span></span>
- <span data-ttu-id="2182a-109">libunwind</span><span class="sxs-lookup"><span data-stu-id="2182a-109">libunwind</span></span>
- <span data-ttu-id="2182a-110">libuuid</span><span class="sxs-lookup"><span data-stu-id="2182a-110">libuuid</span></span>

<span data-ttu-id="2182a-111">Jeśli docelowa wersja OpenSSL środowiska uruchomieniowego to 1,1 lub nowsza, należy zainstalować polecenie **COMPAT-openssl10**.</span><span class="sxs-lookup"><span data-stu-id="2182a-111">If the target runtime environment's OpenSSL version is 1.1 or newer, you'll need to install **compat-openssl10**.</span></span>

<span data-ttu-id="2182a-112">Aby uzyskać więcej informacji o zależnościach, zobacz [samodzielne aplikacje systemu Linux](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span><span class="sxs-lookup"><span data-stu-id="2182a-112">For more information about the dependencies, see [Self-contained Linux apps](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

<span data-ttu-id="2182a-113">W przypadku aplikacji .NET Core, które używają zestawu *System. Drawing. Common* , konieczne będzie również użycie następujących zależności:</span><span class="sxs-lookup"><span data-stu-id="2182a-113">For .NET Core apps that use the *System.Drawing.Common* assembly, you'll also need the following dependency:</span></span>

- [<span data-ttu-id="2182a-114">libgdiplus (wersja 6.0.1 lub nowsza)</span><span class="sxs-lookup"><span data-stu-id="2182a-114">libgdiplus (version 6.0.1 or later)</span></span>](https://www.mono-project.com/docs/gui/libgdiplus/)

  > [!WARNING]
  > <span data-ttu-id="2182a-115">Aby zainstalować najnowszą wersję programu *libgdiplus* , można dodać do systemu repozytorium mono.</span><span class="sxs-lookup"><span data-stu-id="2182a-115">You can install a recent version of *libgdiplus* by adding the Mono repository to your system.</span></span> <span data-ttu-id="2182a-116">Aby uzyskać więcej informacji, zobacz <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="2182a-116">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>
