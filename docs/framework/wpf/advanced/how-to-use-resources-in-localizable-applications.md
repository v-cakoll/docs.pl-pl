---
title: Jak użyć zasobów w zlokalizowanych aplikacjach
ms.date: 03/30/2017
helpviewer_keywords:
- applications [WPF], localizable
- localizable applications [WPF]
ms.assetid: 08539ad6-7fca-4f34-b82b-ff439e11dfa7
ms.openlocfilehash: 8f516a86036656b98add23d38c588b5c19be4d7a
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212478"
---
# <a name="how-to-use-resources-in-localizable-apps"></a><span data-ttu-id="e8d32-102">Instrukcje: korzystanie z zasobów w aplikacjach lokalizowalnych</span><span class="sxs-lookup"><span data-stu-id="e8d32-102">How to: Use resources in localizable apps</span></span>

<span data-ttu-id="e8d32-103">Lokalizacja oznacza adaptację interfejsu użytkownika do różnych kultur.</span><span class="sxs-lookup"><span data-stu-id="e8d32-103">Localization means to adapt a user interface to different cultures.</span></span> <span data-ttu-id="e8d32-104">W tym celu należy przetłumaczyć tekst, taki jak tytuły, podpisy i elementy pola listy.</span><span class="sxs-lookup"><span data-stu-id="e8d32-104">To do this, text such as titles, captions, and list box items must be translated.</span></span> <span data-ttu-id="e8d32-105">Aby ułatwić tłumaczenie, elementy do tłumaczenia są zbierane do plików zasobów.</span><span class="sxs-lookup"><span data-stu-id="e8d32-105">To make translation easier, the items to be translated are collected into resource files.</span></span> <span data-ttu-id="e8d32-106">Zobacz temat [lokalizowanie aplikacji](how-to-localize-an-application.md) , aby uzyskać informacje na temat sposobu tworzenia pliku zasobów na potrzeby lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="e8d32-106">See [Localize an app](how-to-localize-an-application.md) for information on how to create a resource file for localization.</span></span> <span data-ttu-id="e8d32-107">Aby nawiązać aplikację WPF, deweloperzy muszą kompilować wszystkie zasoby lokalizowalne w zestawie zasobów.</span><span class="sxs-lookup"><span data-stu-id="e8d32-107">To make a WPF application localizable, developers need to build all the localizable resources into a resource assembly.</span></span> <span data-ttu-id="e8d32-108">Zestaw zasobów jest zlokalizowany w różnych językach, a związany z nim kod używa interfejsu API zarządzania zasobami do załadowania.</span><span class="sxs-lookup"><span data-stu-id="e8d32-108">The resource assembly is localized into different languages, and the code-behind uses resource management API to load.</span></span>

## <a name="example"></a><span data-ttu-id="e8d32-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="e8d32-109">Example</span></span>

<span data-ttu-id="e8d32-110">Jednym z plików wymaganych dla aplikacji WPF jest plik projektu (. proj).</span><span class="sxs-lookup"><span data-stu-id="e8d32-110">One of the files required for a WPF application is a project file (.proj).</span></span> <span data-ttu-id="e8d32-111">Wszystkie zasoby, które są używane w aplikacji, powinny być uwzględnione w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="e8d32-111">All resources that you use in your application should be included in the project file.</span></span> <span data-ttu-id="e8d32-112">Poniższy przykład kodu XAML pokazuje to.</span><span class="sxs-lookup"><span data-stu-id="e8d32-112">The following XAML example shows this.</span></span>

```xaml
<Resource Include="data\picture1.jpg"/>  
<EmbeddedResource Include="data\stringtable.en-US.restext"/>
```

<span data-ttu-id="e8d32-113">Aby użyć zasobu w aplikacji, Utwórz wystąpienie <xref:System.Resources.ResourceManager> i Załaduj zasób, którego chcesz użyć.</span><span class="sxs-lookup"><span data-stu-id="e8d32-113">To use a resource in your application, instantiate <xref:System.Resources.ResourceManager> and load the resource you want to use.</span></span> <span data-ttu-id="e8d32-114">Poniższy kod w języku C# pokazuje, jak to zrobić.</span><span class="sxs-lookup"><span data-stu-id="e8d32-114">The following C# code demonstrates how to do this.</span></span>

[!code-csharp[LocalizationResources#2](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationResources/CSharp/page1.xaml.cs#2)]

## <a name="see-also"></a><span data-ttu-id="e8d32-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e8d32-115">See also</span></span>

- [<span data-ttu-id="e8d32-116">Lokalizowanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="e8d32-116">Localize an app</span></span>](how-to-localize-an-application.md)
