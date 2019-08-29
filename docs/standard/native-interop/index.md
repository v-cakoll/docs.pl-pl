---
title: Natywna współdziałanie — .NET
description: Dowiedz się, jak interfejsować ze składnikami macierzystymi w programie .NET.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/18/2019
ms.openlocfilehash: 3ca213bc7228d2e4337607df2d47b334c5bea14f
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106807"
---
# <a name="native-interoperability"></a><span data-ttu-id="a9ffe-103">Współdziałanie natywne</span><span class="sxs-lookup"><span data-stu-id="a9ffe-103">Native interoperability</span></span>

<span data-ttu-id="a9ffe-104">W poniższych artykułach przedstawiono różne sposoby wykonywania "natywnych współdziałania" w programie .NET.</span><span class="sxs-lookup"><span data-stu-id="a9ffe-104">The following articles show the various ways of doing "native interoperability" in .NET.</span></span>

<span data-ttu-id="a9ffe-105">Istnieje kilka przyczyn, dla których chcesz wywołać kod natywny:</span><span class="sxs-lookup"><span data-stu-id="a9ffe-105">There are a few reasons why you'd want to call into native code:</span></span>

- <span data-ttu-id="a9ffe-106">Systemy operacyjne korzystają z dużej liczby interfejsów API, które nie znajdują się w zarządzanych bibliotekach klas.</span><span class="sxs-lookup"><span data-stu-id="a9ffe-106">Operating systems come with a large volume of APIs that aren't present in the managed class libraries.</span></span> <span data-ttu-id="a9ffe-107">Głównym przykładem tego scenariusza będzie dostęp do funkcji zarządzania sprzętem lub systemem operacyjnym.</span><span class="sxs-lookup"><span data-stu-id="a9ffe-107">A prime example for this scenario would be access to hardware or operating system management functions.</span></span>
- <span data-ttu-id="a9ffe-108">Komunikacja z innymi składnikami, które mają lub mogą tworzyć interfejsy ABI w stylu C (natywny interfejsy ABI), takie jak kod Java, który jest udostępniany za pośrednictwem [natywnego interfejsu Java (JNI)](https://docs.oracle.com/javase/8/docs/technotes/guides/jni/) lub dowolnego innego języka zarządzanego, który może generować składnik macierzysty.</span><span class="sxs-lookup"><span data-stu-id="a9ffe-108">Communicating with other components that have or can produce C-style ABIs (native ABIs), such as Java code that is exposed via [Java Native Interface (JNI)](https://docs.oracle.com/javase/8/docs/technotes/guides/jni/) or any other managed language that could produce a native component.</span></span>
- <span data-ttu-id="a9ffe-109">W systemie Windows większość oprogramowania instalowanego, takiego jak pakiet Microsoft Office, rejestruje składniki COM, które reprezentują swoje programy, i umożliwia deweloperom ich automatyzację lub korzystanie z nich.</span><span class="sxs-lookup"><span data-stu-id="a9ffe-109">On Windows, most of the software that gets installed, such as the Microsoft Office suite, registers COM components that represent their programs and allow developers to automate them or use them.</span></span> <span data-ttu-id="a9ffe-110">Wymaga to również natywnej współdziałania.</span><span class="sxs-lookup"><span data-stu-id="a9ffe-110">This also requires native interoperability.</span></span>

<span data-ttu-id="a9ffe-111">Poprzednia lista nie obejmuje wszystkich potencjalnych sytuacji i scenariuszy, w których deweloper powinien chcieć/lubić, jak ma to być interfejs ze składnikami macierzystymi.</span><span class="sxs-lookup"><span data-stu-id="a9ffe-111">The previous list doesn't cover all of the potential situations and scenarios in which the developer would want/like/need to interface with native components.</span></span> <span data-ttu-id="a9ffe-112">Biblioteka klas .NET, na przykład, używa natywnej obsługi współdziałania w celu zaimplementowania uczciwej liczby interfejsów API, takich jak obsługa konsoli i manipulowanie, dostęp do systemu plików i inne.</span><span class="sxs-lookup"><span data-stu-id="a9ffe-112">.NET class library, for instance, uses the native interoperability support to implement a fair number of its APIs, like console support and manipulation, file system access and others.</span></span> <span data-ttu-id="a9ffe-113">Należy jednak pamiętać, że w razie potrzeby jest dostępna opcja.</span><span class="sxs-lookup"><span data-stu-id="a9ffe-113">However, it's important to note that there's an option if needed.</span></span>

> [!NOTE]
> <span data-ttu-id="a9ffe-114">Większość przykładów w tej sekcji zostanie przedstawionych dla wszystkich trzech obsługiwanych platform dla platformy .NET Core (Windows, Linux i macOS).</span><span class="sxs-lookup"><span data-stu-id="a9ffe-114">Most of the examples in this section will be presented for all three supported platforms for .NET Core (Windows, Linux and macOS).</span></span> <span data-ttu-id="a9ffe-115">Jednakże w przypadku niektórych krótkich i ilustracyjnych przykładów jest wyświetlany tylko jeden przykład, w którym są używane nazwy i rozszerzenia systemu Windows (czyli "dll" dla bibliotek).</span><span class="sxs-lookup"><span data-stu-id="a9ffe-115">However, for some short and illustrative examples, just one sample is shown that uses Windows filenames and extensions (that is, "dll" for libraries).</span></span> <span data-ttu-id="a9ffe-116">Nie oznacza to, że te funkcje nie są dostępne w systemie Linux lub macOS, zostały wykonane tylko w celu wygody.</span><span class="sxs-lookup"><span data-stu-id="a9ffe-116">This doesn't mean that those features aren't available on Linux or macOS, it was done merely for convenience sake.</span></span>

## <a name="see-also"></a><span data-ttu-id="a9ffe-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a9ffe-117">See also</span></span>

- [<span data-ttu-id="a9ffe-118">Wywołanie platformy (P/Invoke)</span><span class="sxs-lookup"><span data-stu-id="a9ffe-118">Platform Invoke (P/Invoke)</span></span>](pinvoke.md)
- [<span data-ttu-id="a9ffe-119">Kierowanie typów</span><span class="sxs-lookup"><span data-stu-id="a9ffe-119">Type marshaling</span></span>](type-marshaling.md)
- [<span data-ttu-id="a9ffe-120">Najlepsze rozwiązania w zakresie współdziałania natywnego</span><span class="sxs-lookup"><span data-stu-id="a9ffe-120">Native interoperability best practices</span></span>](best-practices.md)
