Select sum(qty) as total_units
,sum(case when qty <= 3 then qty else 0 end) as units_with_3_or_less
,datediff(day,getdate(),convert(date,c.required_despatch_time)) as "Days to Process"
from x_pick p
left join x_consignment c on p.order_id =c.order_id
and order_id like '5%'
