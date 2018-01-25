# Translate

## Synopsis
A Neuron to translate sentence with Google API

## Installation

```bash
intelora install --git-url https://github.com/intelora/neuron_translate.git
```

## Options

| parameter | required | default | choices                                | comments                                                                       |
|-----------|----------|---------|----------------------------------------|--------------------------------------------------------------------------------|
| lang_out  | yes      |         | E.g: "en", "fr", "Spanish", "Français" | Language to translate sentence: langage id ("en") or language name ("Spanish") |
| lang_in   | no       |  auto   | E.g: "auto", "en", "fr"                | Language of original sentence: "auto" for automatique detection or lang id     |
| sentence  | yes      |         |                                        | Sentence translate                                                             |

## Return Values

| Name     | Description           | Type   | sample          |
|----------|-----------------------|--------|-----------------|
| result   | Result of translation | string | "Buenas noches" |
| lang_in  | lang id in            | string | "en"            |
| lang_out | lang id out           | string | "es"            |


## Limitation
Only available languages for translation:
-English
-Spansih
-French


## Synapses example

```yml
  - name: "en-translate-es"
    signals:
      - order: "translate {{sentence}} in Spanish"
    neurons:
      - translate:
          lang_in: "en"
          lang_out: "es"
          args:
            - sentence
          say_template: "{{ result }}"

  - name: "en-translate-fr"
    signals:
      - order: "translate {{sentence}} in French"
    neurons:
      - translate:
          lang_in: "en"
          lang_out: "fr"
          args:
            - sentence
          say_template: "{{ result }}"
```

