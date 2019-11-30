```plantuml
left to right direction
skinparam packageStyle rectangle

rectangle system_do_komunikacji {
  customer -- (checkout)
  (checkout) .> (payment) : include
  (help) .> (checkout) : extends
  (checkout) -- clerk
}

actor MIP
actor Jednostka_Administracyjna
MIP--Jednostka_Administracyjna

```