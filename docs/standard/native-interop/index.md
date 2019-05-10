---
title: Współdziałanie natywne — .NET
description: Dowiedz się, jak współpracować z usługą składnikami macierzystymi na platformie .NET.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/18/2019
ms.openlocfilehash: b01ea9c17db6da32755309d9c1c2359cecaa1155
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/06/2019
ms.locfileid: "65062714"
---
# <a name="native-interoperability"></a><span data-ttu-id="6867c-103">Współdziałanie natywne</span><span class="sxs-lookup"><span data-stu-id="6867c-103">Native interoperability</span></span>

<span data-ttu-id="6867c-104">Następujące artykuły pokazują różne sposoby wykonywania "interoperacyjności macierzystej" na platformie .NET.</span><span class="sxs-lookup"><span data-stu-id="6867c-104">The following articles show the various ways of doing "native interoperability" in .NET.</span></span>

<span data-ttu-id="6867c-105">Istnieje kilka powodów dlaczego warto mogą wywoływać kodu natywnego:</span><span class="sxs-lookup"><span data-stu-id="6867c-105">There are a few reasons why you'd want to call into native code:</span></span>

* <span data-ttu-id="6867c-106">Systemy operacyjne są dostarczane z dużą liczbą interfejsów API, które nie są obecne w bibliotekach klas zarządzanych.</span><span class="sxs-lookup"><span data-stu-id="6867c-106">Operating systems come with a large volume of APIs that aren't present in the managed class libraries.</span></span> <span data-ttu-id="6867c-107">Podstawowy przykład w tym scenariuszu będzie dostęp do sprzętu lub systemu operacyjnego, funkcji zarządzania.</span><span class="sxs-lookup"><span data-stu-id="6867c-107">A prime example for this scenario would be access to hardware or operating system management functions.</span></span>
* <span data-ttu-id="6867c-108">Podczas komunikowania się z innymi składnikami, które lub może tworzyć interfejsy ABI stylu języka C (natywnych interfejsów ABI), takie jak kod Java, który jest uwidaczniany za pomocą [interfejsem Java Native Interface (JNI)](https://docs.oracle.com/javase/8/docs/technotes/guides/jni/) lub dowolnym innym języku zarządzanych, które może powodować składnika macierzystego.</span><span class="sxs-lookup"><span data-stu-id="6867c-108">Communicating with other components that have or can produce C-style ABIs (native ABIs), such as Java code that is exposed via [Java Native Interface (JNI)](https://docs.oracle.com/javase/8/docs/technotes/guides/jni/) or any other managed language that could produce a native component.</span></span>
* <span data-ttu-id="6867c-109">W Windows większość oprogramowania instalowanego, takich jak pakiet Microsoft Office rejestruje składników COM, które reprezentują swoich programów i umożliwiają deweloperom Automatyzowanie je lub używać ich.</span><span class="sxs-lookup"><span data-stu-id="6867c-109">On Windows, most of the software that gets installed, such as the Microsoft Office suite, registers COM components that represent their programs and allow developers to automate them or use them.</span></span> <span data-ttu-id="6867c-110">Wymaga to interoperacyjności macierzystej.</span><span class="sxs-lookup"><span data-stu-id="6867c-110">This also requires native interoperability.</span></span>

<span data-ttu-id="6867c-111">Poprzedniej liście nie obejmuje wszystkich potencjalnych sytuacji i scenariusze, w których deweloper może chcesz/podobne/potrzebę do połączenia interfejsem z składnikami macierzystymi.</span><span class="sxs-lookup"><span data-stu-id="6867c-111">The previous list doesn't cover all of the potential situations and scenarios in which the developer would want/like/need to interface with native components.</span></span> <span data-ttu-id="6867c-112">Biblioteka klas programu .NET, na przykład korzysta z obsługi interoperacyjności macierzystej zaimplementować podejście liczbę interfejsów API, takich jak obsługa konsoli i manipulowania, dostęp do systemu plików i inne.</span><span class="sxs-lookup"><span data-stu-id="6867c-112">.NET class library, for instance, uses the native interoperability support to implement a fair number of its APIs, like console support and manipulation, file system access and others.</span></span> <span data-ttu-id="6867c-113">Jest jednak należy pamiętać, że jest dostępna opcja w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="6867c-113">However, it's important to note that there's an option if needed.</span></span>

> [!NOTE]
> <span data-ttu-id="6867c-114">Większość przykładów w tej sekcji zostaną przedstawione na potrzeby wszystkich trzech obsługiwanych platform dla platformy .NET Core (Windows, Linux i macOS).</span><span class="sxs-lookup"><span data-stu-id="6867c-114">Most of the examples in this section will be presented for all three supported platforms for .NET Core (Windows, Linux and macOS).</span></span> <span data-ttu-id="6867c-115">Kilka przykładów krótki i opisowy tylko jeden przykład jest jednak wyświetlany korzystający Windows nazwy plików i rozszerzenia (czyli "dll" jak biblioteki).</span><span class="sxs-lookup"><span data-stu-id="6867c-115">However, for some short and illustrative examples, just one sample is shown that uses Windows filenames and extensions (that is, "dll" for libraries).</span></span> <span data-ttu-id="6867c-116">Nie oznacza to, że te funkcje nie są dostępne w systemie Linux lub macOS, została wykonana jedynie dla wygody sake.</span><span class="sxs-lookup"><span data-stu-id="6867c-116">This doesn't mean that those features aren't available on Linux or macOS, it was done merely for convenience sake.</span></span>

## <a name="see-also"></a><span data-ttu-id="6867c-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6867c-117">See also</span></span>

- [<span data-ttu-id="6867c-118">Wywołanie platformy (P/Invoke)</span><span class="sxs-lookup"><span data-stu-id="6867c-118">Platform Invoke (P/Invoke)</span></span>](pinvoke.md)
- [<span data-ttu-id="6867c-119">Marshaling typów</span><span class="sxs-lookup"><span data-stu-id="6867c-119">Type marshaling</span></span>](type-marshaling.md)
- [<span data-ttu-id="6867c-120">Współdziałanie natywne najlepszych rozwiązań</span><span class="sxs-lookup"><span data-stu-id="6867c-120">Native interoperability best practices</span></span>](best-practices.md)
