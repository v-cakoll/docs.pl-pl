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
# <a name="how-to-use-resources-in-localizable-apps"></a>Instrukcje: korzystanie z zasobów w aplikacjach lokalizowalnych

Lokalizacja oznacza adaptację interfejsu użytkownika do różnych kultur. W tym celu należy przetłumaczyć tekst, taki jak tytuły, podpisy i elementy pola listy. Aby ułatwić tłumaczenie, elementy do tłumaczenia są zbierane do plików zasobów. Zobacz temat [lokalizowanie aplikacji](how-to-localize-an-application.md) , aby uzyskać informacje na temat sposobu tworzenia pliku zasobów na potrzeby lokalizacji. Aby nawiązać aplikację WPF, deweloperzy muszą kompilować wszystkie zasoby lokalizowalne w zestawie zasobów. Zestaw zasobów jest zlokalizowany w różnych językach, a związany z nim kod używa interfejsu API zarządzania zasobami do załadowania.

## <a name="example"></a>Przykład

Jednym z plików wymaganych dla aplikacji WPF jest plik projektu (. proj). Wszystkie zasoby, które są używane w aplikacji, powinny być uwzględnione w pliku projektu. Poniższy przykład kodu XAML pokazuje to.

```xaml
<Resource Include="data\picture1.jpg"/>  
<EmbeddedResource Include="data\stringtable.en-US.restext"/>
```

Aby użyć zasobu w aplikacji, Utwórz wystąpienie <xref:System.Resources.ResourceManager> i Załaduj zasób, którego chcesz użyć. Poniższy kod w języku C# pokazuje, jak to zrobić.

[!code-csharp[LocalizationResources#2](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationResources/CSharp/page1.xaml.cs#2)]

## <a name="see-also"></a>Zobacz też

- [Lokalizowanie aplikacji](how-to-localize-an-application.md)
