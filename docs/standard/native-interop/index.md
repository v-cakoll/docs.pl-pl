---
title: Współdziałanie natywne — .NET
description: Dowiedz się, jak współpracować z usługą składnikami macierzystymi na platformie .NET.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/18/2019
ms.openlocfilehash: 85a22394c8c59f51f462bc0a2ba6a11265682db3
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2019
ms.locfileid: "54416242"
---
# <a name="native-interoperability"></a><span data-ttu-id="8d814-103">Współdziałanie natywne</span><span class="sxs-lookup"><span data-stu-id="8d814-103">Native interoperability</span></span>

<span data-ttu-id="8d814-104">Następujące artykuły pokazują różne sposoby wykonywania "interoperacyjności macierzystej" na platformie .NET.</span><span class="sxs-lookup"><span data-stu-id="8d814-104">The following articles show the various ways of doing "native interoperability" in .NET.</span></span>

<span data-ttu-id="8d814-105">Istnieje kilka powodów dlaczego warto mogą wywoływać kodu natywnego:</span><span class="sxs-lookup"><span data-stu-id="8d814-105">There are a few reasons why you'd want to call into native code:</span></span>

* <span data-ttu-id="8d814-106">Systemy operacyjne są dostarczane z dużą liczbą interfejsów API, które nie są obecne w bibliotekach klas zarządzanych.</span><span class="sxs-lookup"><span data-stu-id="8d814-106">Operating systems come with a large volume of APIs that aren't present in the managed class libraries.</span></span> <span data-ttu-id="8d814-107">Podstawowy przykład w tym scenariuszu będzie dostęp do sprzętu lub systemu operacyjnego, funkcji zarządzania.</span><span class="sxs-lookup"><span data-stu-id="8d814-107">A prime example for this scenario would be access to hardware or operating system management functions.</span></span>
* <span data-ttu-id="8d814-108">Podczas komunikowania się z innymi składnikami, które lub może tworzyć interfejsy ABI stylu języka C (natywnych interfejsów ABI), takie jak kod Java, który jest uwidaczniany za pomocą [interfejsem Java Native Interface (JNI)](https://docs.oracle.com/javase/8/docs/technotes/guides/jni/) lub dowolnym innym języku zarządzanych, które może powodować składnika macierzystego.</span><span class="sxs-lookup"><span data-stu-id="8d814-108">Communicating with other components that have or can produce C-style ABIs (native ABIs), such as Java code that is exposed via [Java Native Interface (JNI)](https://docs.oracle.com/javase/8/docs/technotes/guides/jni/) or any other managed language that could produce a native component.</span></span>
* <span data-ttu-id="8d814-109">W Windows większość oprogramowania instalowanego, takich jak pakiet Microsoft Office rejestruje składników COM, które reprezentują swoich programów i umożliwiają deweloperom Automatyzowanie je lub używać ich.</span><span class="sxs-lookup"><span data-stu-id="8d814-109">On Windows, most of the software that gets installed, such as the Microsoft Office suite, registers COM components that represent their programs and allow developers to automate them or use them.</span></span> <span data-ttu-id="8d814-110">Wymaga to interoperacyjności macierzystej.</span><span class="sxs-lookup"><span data-stu-id="8d814-110">This also requires native interoperability.</span></span>

<span data-ttu-id="8d814-111">Poprzedniej liście nie obejmuje wszystkich potencjalnych sytuacji i scenariusze, w których deweloper może chcesz/podobne/potrzebę do połączenia interfejsem z składnikami macierzystymi.</span><span class="sxs-lookup"><span data-stu-id="8d814-111">The previous list doesn't cover all of the potential situations and scenarios in which the developer would want/like/need to interface with native components.</span></span> <span data-ttu-id="8d814-112">Biblioteka klas programu .NET, na przykład korzysta z obsługi interoperacyjności macierzystej zaimplementować podejście liczbę interfejsów API, takich jak obsługa konsoli i manipulowania, dostęp do systemu plików i inne.</span><span class="sxs-lookup"><span data-stu-id="8d814-112">.NET class library, for instance, uses the native interoperability support to implement a fair number of its APIs, like console support and manipulation, file system access and others.</span></span> <span data-ttu-id="8d814-113">Jest jednak należy pamiętać, że jest dostępna opcja w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="8d814-113">However, it's important to note that there's an option if needed.</span></span>

> [!NOTE]
> <span data-ttu-id="8d814-114">Większość przykładów w tej sekcji zostaną przedstawione na potrzeby wszystkich trzech obsługiwanych platform dla platformy .NET Core (Windows, Linux i macOS).</span><span class="sxs-lookup"><span data-stu-id="8d814-114">Most of the examples in this section will be presented for all three supported platforms for .NET Core (Windows, Linux and macOS).</span></span> <span data-ttu-id="8d814-115">Kilka przykładów krótki i opisowy tylko jeden przykład jest jednak wyświetlany korzystający Windows nazwy plików i rozszerzenia (czyli "dll" jak biblioteki).</span><span class="sxs-lookup"><span data-stu-id="8d814-115">However, for some short and illustrative examples, just one sample is shown that uses Windows filenames and extensions (that is, "dll" for libraries).</span></span> <span data-ttu-id="8d814-116">Nie oznacza to, że te funkcje nie są dostępne w systemie Linux lub macOS, została wykonana jedynie dla wygody sake.</span><span class="sxs-lookup"><span data-stu-id="8d814-116">This doesn't mean that those features aren't available on Linux or macOS, it was done merely for convenience sake.</span></span>

## <a name="see-also"></a><span data-ttu-id="8d814-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8d814-117">See also</span></span>

- [<span data-ttu-id="8d814-118">Wywołanie platformy (P/Invoke)</span><span class="sxs-lookup"><span data-stu-id="8d814-118">Platform Invoke (P/Invoke)</span></span>](pinvoke.md)
- [<span data-ttu-id="8d814-119">Typ zarządzany</span><span class="sxs-lookup"><span data-stu-id="8d814-119">Type marshalling</span></span>](type-marshalling.md)
